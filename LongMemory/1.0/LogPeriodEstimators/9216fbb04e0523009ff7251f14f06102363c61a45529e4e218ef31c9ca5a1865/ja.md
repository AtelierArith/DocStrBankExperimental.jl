```
exact_whittle_est_variance(x::Array; m::Real=0.8)
```

時系列 `x` の長期記憶パラメータの推定量の分散を、正確なウィトル対数尤度関数を使用して推定します。

# 引数

  * `x::Vector`: 時系列

# オプション引数

  * `m∈(0,1)::Float64`: テーパーの最終値。デフォルトは0.8

# 出力

  * `varb::Float64`: 推定量の分散

# 注意事項

計算には多重ディスパッチが使用されます。最初の入力が整数の場合、関数はそれをサンプルサイズとして解釈します。それ以外の場合、時系列の長さからサンプルサイズを計算します。分散は、ウィトル対数尤度関数を使用した場合と同じです。

# 例

```julia-repl
julia> exact_whittle_est_variance(fi(100,0.4))
```
