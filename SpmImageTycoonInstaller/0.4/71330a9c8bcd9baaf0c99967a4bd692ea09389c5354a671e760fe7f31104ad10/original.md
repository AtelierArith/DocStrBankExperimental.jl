```
install(dir::String=""; ver::String="main", shortcuts_only::Bool=false,
    interactive::Bool=true, debug::Bool=false, test::Bool=false)::Nothing
```

Installs SpmImageTycoon.

A specific directory can be directly given as `dir`.

`ver` specifies the version to install: `"main"` (default), `"dev"` for the development version, `"local"` for the locally installed version of `SpmImageTycoon`.

If `shortcuts_only` is  `true`. then only shortcuts will be installed - not the app itself (use this only if you installed the app before - otherwise the shortcuts won't work). If `interactive` is `false`, then the install will proceed without user interaction. If 'debug' is `true`, then the behind-the-scenes output of the installation will be shown (instead of written to a log file). If `test` is `true`, then installation will only be simulated and compilation will be skipped.
