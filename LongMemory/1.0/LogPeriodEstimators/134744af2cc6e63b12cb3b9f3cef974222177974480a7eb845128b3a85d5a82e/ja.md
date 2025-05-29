```
gph_est(x::Array; m::Real=0.8, l=0, br=0::Int)
```

時系列 `x` の長期記憶パラメータを対数周期ogram推定量を使用して推定します。詳細については、[Geweke and Porter-Hudak (1983)](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9892.1983.tb00371.x) および [Andrews and Guggenberger (2003)](https://www.jstor.org/stable/3082070) を参照してください。

# 引数

  * `x::Vector`: 時系列
  * `m∈(0,1)::Float64`: テーパー最終
  * `l∈(0,1)::Float64`: テーパー初期
  * `br::Int64`: バイアス削減項の数

# 出力

  * `d::Float64`: 長期記憶パラメータ

# 注意事項

この関数は、時系列 `x` の周期ogramを周波数 `[T^l,T^m]` の範囲で考慮します。ゼロ周波数は常に除外されます。`m` と `l` のデフォルト値はそれぞれ 0.8 と 0 です。条件 `m < l` が成り立つ必要があります。

`br` のデフォルト値は 0 で、元の GPH 対数周期ogram推定量を返します。

# 例

```julia-repl
julia> gph_est(randn(100,1))
```
