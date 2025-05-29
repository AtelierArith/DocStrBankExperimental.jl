```
mixing(model::EoSModel, p, T, z=SA[1.], property; phase=:unknown, threaded=true, vol0=nothing)
```

指定されたプロパティの混合関数を次のように計算します：

```julia
f_mix = f(p,T,z) - ∑zᵢ*f_pureᵢ(p,T)
```

キーワード `phase`、`threaded` および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
