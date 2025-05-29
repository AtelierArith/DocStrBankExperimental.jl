```
fig = gangoffourplot(P::LTISystem, C::LTISystem; minimal=true, plotphase=false, Ms_lines = [1.0, 1.25, 1.5], Mt_lines = [], sigma = true, kwargs...)
```

Gang-of-Four プロット。

`sigma` は、MIMO `S` と `T` のために [`bodeplot`](@ref) の代わりに [`sigmaplot`](@ref) が使用されるかどうかを決定します。`kwargs` は RecipesBase.plot への引数として送信されます。
