```
@usingtmp 
@usingtmp pkg
@usingtmp pkg1, pkg2, ... 
@usingtmp pkg: fn
@usingtmp pkg: fn, @mcr, ...
```

Activates a temporary environment, optionally installs packages into it and loads them with `using` keyword. 

  * If current environment is a temporary one, environment is not changed.
  * If current env was a project (not package!), a temporary env will be activated.
  * If current env was a package (under development), e.g. `MyPkg`, a temporary env will be activated, AND `MyPkg` will be `dev`-ed in that temporary env.

Afterwards, if `@usingtmp` was called with arguments, the corresponding packages will be installed into that temporary env,  and imported with `using` keyword.

This macro is exported.
