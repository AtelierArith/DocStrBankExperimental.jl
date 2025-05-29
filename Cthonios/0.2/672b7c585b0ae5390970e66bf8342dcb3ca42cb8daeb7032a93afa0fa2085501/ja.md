```julia
DirichletBC(
    inputs::Dict{Symbol, Any}
) -> Cthonios.DirichletBC{_A, _B, F} where {_A, _B, F<:RuntimeGeneratedFunctions.RuntimeGeneratedFunction}

```

入力ファイルの構文

```
domain:
  dirichlet 境界条件:
  - type: DirichletBC
    nodeset: nset_1
    function: (x, t) -> 0.0
  - type: DirichletBC
    nodeset: nset_2
    function: (x, t) -> 1.0
  ...
```
