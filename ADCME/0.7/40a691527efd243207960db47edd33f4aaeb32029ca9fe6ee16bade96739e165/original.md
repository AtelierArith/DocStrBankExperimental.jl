```
install(s::String; force::Bool = false, islocal::Bool = false)
```

Install a custom operator from a URL, a directory (when `islocal` is true), or a string. In any of the three case,  `install` copy the folder to /home/terasaki/.julia/packages/ADCME/94vEM/deps/CustomOps/Plugin.  When `s` is a string, `s` is converted to 

https://github.com/ADCMEMarket/<s>
