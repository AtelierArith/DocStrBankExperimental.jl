```
Indicator(col; k=10, scale=:quantile, categ=false)
```

連続変数を、指定された `scale` の `col` 値の半区間によって定義された `k` 個の指標変数に変換します。オプションで、`categ` オプションを指定すると、生の 1 と 0 の代わりにバイナリのカテゴリ値を返します。

増加する閾値のシーケンス `t1 < t2 < ... < tk` が与えられた場合、指標変換は連続変数 `Z` を `k` 個の変数 `Z_1 = Z <= t1`, `Z_2 = Z <= t2`, ..., `Z_k = Z <= tk` に変換します。

## スケール:

  * `:quantile` - 閾値は、確率の線形範囲を使用して `quantile(Z, p)` 関数を用いて計算されます。
  * `:linear` - 閾値は、線形範囲を使用して計算されます。

# 例

```julia
Indicator(1, k=3)
Indicator(:a, k=6, scale=:linear)
Indicator("a", k=9, scale=:linear, categ=true)
```
