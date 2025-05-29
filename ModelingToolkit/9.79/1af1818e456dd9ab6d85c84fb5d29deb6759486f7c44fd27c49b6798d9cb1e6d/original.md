```julia
connect(
    var1::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr},
    var2::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr},
    vars::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr}...
) -> Symbolics.Equation

```

Connect multiple causal variables. The first variable must be an output, and all subsequent variables must be inputs. The statement `connect(var1, var2, var3, ...)` expands to:

```julia
var1 ~ var2
var1 ~ var3
# ...
```
