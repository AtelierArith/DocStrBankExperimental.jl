```
fi_ar_coefs(d::Real, maxlags::Int)
```

パラメータ `d` を持つ分数差分過程のAR係数をラグ 1, ..., `maxlags` で計算します。

# 引数

  * `d::Real`: 分数差分パラメータ。
  * `maxlags::Int`: 計算するラグの数。

# 出力

  * `ar_coefs::Array`: パラメータ `d` を持つ分数差分過程のAR係数で、ラグ 1, ..., `maxlags` での値。

# 注意事項

AR係数は速度のために再帰的な公式を使用して計算されます。ゼロラグ係数は計算されず、理論的には 1 です。

# 例

```julia
julia> fi_ar_coefs(0.2, 5)
```
