```
lm_change_test(y::Array; uplim::Real = 0.15, lowlim::Real = 0.15)
```

構造変化の位置を長期メモリモデルで推定します。

# 引数

  * `y::Array`: テストされる系列。

# オプション引数

  * `uplim::Real = 0.15`: テストされる系列の上限割合。
  * `lowlim::Real = 0.15`: テストされる系列の下限割合。

# 出力

  * `τ::Int`: 構造変化の推定位置。

# 例

```julia-repl
julia> lm_change_test(randn(100))
```

# 注意事項

この関数は、長期メモリモデルにおける構造変化の位置を推定します。この関数は、ホイットル推定量を使用して長期メモリパラメータを推定します。次に、系列を統合し、統合された系列をスター付き系列に対するOLS回帰のt統計量を計算します。この関数は、前方および後方のt統計量を計算し、最大の二乗t統計量の位置を返します。したがって、変化の方向に対してロバストです。

# 参考文献

Martins and Rodrigues (2014), "Testing for persistence change in fractionally integrated models: An application to world inflation rates", Computational Statistics and Data Analysis, 76.
