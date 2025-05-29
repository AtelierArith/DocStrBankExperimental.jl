```
write_xsf(filename::String, wfc::WannierFunction, str::Structure; value_func=x->norm(x))
```

Writes a [`WannierFunction`](@ref) and [`Structure`](https://louisponet.github.io/DFControl.jl/stable/guide/structure/) to an xsf file that is readable by XCrysden or VESTA. The values that are written can be controlled by `value_func` that gets used on each entry of `wfc.values` and should output a single `Number`. 
