```
entropy_dispersion(x; base = 2, kwargs...)
```

分散エントロピーを計算します。この関数は、単に次の関数への便利な呼び出しです：

```julia
est = Dispersion(kwargs...)
information(Shannon(base), est, x)
```

詳細については[`Dispersion`](@ref)を参照してください。
