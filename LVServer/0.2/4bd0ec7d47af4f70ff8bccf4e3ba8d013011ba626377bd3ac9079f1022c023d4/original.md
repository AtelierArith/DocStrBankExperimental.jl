```
setglobals(;isOK, extant=scriptexists, excpn = nothing)
```

Set the globals of the `LVServer` module. By default do not change the value of `scriptexists`. Use this function from the top-level scripts, e.g. as executing from LabVIEW.

# Examples

```julia-repl

julia> setglobals(;isOK=true, extant=true);

```
