```
qstart(;debug = false, qwtw_test = false, libraryName = "libqwtw", marblePluginPath = "")::Int32
```

starts the qwtw "C" library.   Without it, nothing will work. Call it before any other functions.  

  * if debug, will try to enable debug print out. A lot of info. Just for debugging.
  * qwtw_test	-> if true, will try to not modify env variables.
  * libraryName: if not empty, then use this a a library name instead of the library from artifact (for debugging)
  * marblePluginPath alternative location for 'Marble plugins'. In case you have your own build of the Marble library (used for drawing a map).

return 0 if success
