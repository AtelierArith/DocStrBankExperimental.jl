```
tab(X::AbstractArray)
tab(X::DataFrame; vary = nothing)
```

カテゴリ変数のタブulation。

  * `x` : カテゴリ変数またはカテゴリ変数を含むデータセット。

データセットに特有のもの：

  * `vary` : `X` で考慮するグループ変数の名前のベクター（デフォルトでは `X` のすべての列）。

出力にはソートされたレベルが含まれます。

## 例

```julia
using Jchemo, DataFrames

x = rand(["a"; "b"; "c"], 20)
res = tab(x)
res.keys
res.vals

n = 20
X = hcat(rand(1:2, n), rand(["a", "b", "c"], n))
df = DataFrame(X, [:v1, :v2])

tab(X[:, 2])
tab(string.(X))

tab(df)
tab(df; vary = [:v1, :v2])
tab(df; vary = :v2)
```
