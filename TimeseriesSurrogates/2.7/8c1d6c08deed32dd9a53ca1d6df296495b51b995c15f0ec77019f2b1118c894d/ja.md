```
pvalue(test::SurrogateTest; tail = :left)
```

与えられた [`SurrogateTest`](@ref) に対応する [p値](https://en.wikipedia.org/wiki/P-value) を返します。オプションで、どの種類の片側検定を行うかを指定できます（`:left, :right, :both` のいずれか）。

[`SurrogateTest`](@ref) に対して、p値は単にサロゲート統計量が入力データから計算された識別統計量を超える（`tail = :right` の場合）か、または下回る（`tail = :left` の場合）割合です。

`tail` のデフォルト値は、サロゲートデータがより高い識別統計量の値を持つと予想されることを前提としています。これはエントロピーを定量化する統計量に当てはまります。自己相関を定量化する統計量の場合は、`tail = :right` を使用してください。
