# Setup.JS #

Manage library folders and external dependency folders in your project
by including setup.js.  Call it from the beginning of your project's
entry-point to adjust `require.paths`.

For example, if you're making an application structured like this:

    README
    app.js  # main program
    ext/    # third-party libraries, git submodules, etc.
    lib/    # your code

Drop setup.js into ext and add this as the first line of app.js:

    require('./ext/setup').app(__dirname);

Now anything in lib or ext is fully accessible.  If your
project is a library rather than an application, it might be
structured this way:

    README
    ext/
    lib/mylib.js
    lib/mylib/

Put setup.js into ext, then make this the first line of mylib.js:

    require('../ext/setup').app(__dirname + '/..');

Don't forget to `node-waf` any C++ extensions in ext!
