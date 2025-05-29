```
predict_proba{V<:Number}(m::HybridNB, f_c::Vector{Vector{Float64}}, f_d::Vector{Vector{Int64}})
```

入力特徴に対する対数確率を予測します。予測されたクラスとその対数確率の推定値のタプルを返します。
