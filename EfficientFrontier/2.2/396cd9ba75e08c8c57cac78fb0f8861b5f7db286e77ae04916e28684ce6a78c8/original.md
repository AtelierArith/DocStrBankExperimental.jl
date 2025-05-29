```
    SimplexLP(PS::Problem; settings=Simplex.Settings(PS), min=true)
```

find the `Status` for assets by simplex method. If `min=false`, we maximize the objective function

See also [`StatusSwitchingQP.Status`](@ref), [`Problem`](@ref), [`StatusSwitchingQP.Settings`](@ref), [`StatusSwitchingQP.Simplex.cDantzigLP`](@ref), [`StatusSwitchingQP.Simplex.maxImprvLP`](@ref)
