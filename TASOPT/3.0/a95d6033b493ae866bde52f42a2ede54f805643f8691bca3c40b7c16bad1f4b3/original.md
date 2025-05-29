```
size_aircraft(ac::aircraft; iter=35, initwgt=false, Ldebug=false,
    printiter=true, saveOD=false)
```

sizes the given `aircraft` instance. A light wrapper around the `_size_aircraft!` function, which does the actual work.
