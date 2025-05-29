```
@using LongModuleName as alias
```

Load the module `LongModuleName` with `using` and binds it to `alias`. Roughly equivalent to

```julia
using LongModuleName
const alias = LongModuleName
```
