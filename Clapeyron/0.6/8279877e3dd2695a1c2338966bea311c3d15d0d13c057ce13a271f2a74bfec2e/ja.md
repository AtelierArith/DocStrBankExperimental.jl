```
activity(model::EoSModel,p,T,z=SA[1.0];reference = :pure, phase=:unknown, threaded=true, vol0=nothing)
```

活動を計算します。活動は次のように定義されます：

```julia
log(a) = (μ_mixt - μ_ref) / R̄ / T
```

ここで `μ_mixt` は混合物の化学ポテンシャルであり、`μ_ref` は `p`,`T` 条件下でのモデルの参照化学ポテンシャルで、[`Clapeyron.reference_chemical_potential`](@ref)を介して計算されます。内部的には、[`Clapeyron.volume`](@ref)を呼び出して `V` を取得し、`VT_fugacity_coefficient(model,V,T,z)`を介して特性を計算します。

キーワード `phase`、`threaded`、および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。

`μ_ref` キーワード引数が提供されていない場合、`reference` キーワードが参照化学ポテンシャルを指定するために使用されます。
