```
gph_est_variance(x::Array; m::Real=0.8, l=0, br=0::Int)
```

時系列 `x` の長期記憶パラメータの分散を対数周期グラム推定量を用いて推定します。詳細については、[Geweke and Porter-Hudak (1983)](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9892.1983.tb00371.x) および [Andrews and Guggenberger (2003)](https://www.jstor.org/stable/3082070) を参照してください。

# 引数

  * `x::Vector`: 時系列

# オプション引数

  * `m∈(0,1)::Float64`: テーパーの最終値。デフォルトは 0.8
  * `br::Int64`: バイアス削減項の数

# 出力

  * `varb::Float64`: 長期記憶パラメータの分散

# 注意事項

計算には多重ディスパッチが使用されます。最初の入力が整数の場合、関数はそれをサンプルサイズとして解釈します。それ以外の場合、時系列の長さからサンプルサイズを計算します。

# 例

```julia-repl
julia> gph_est_variance(fi(100,0.4))
```
