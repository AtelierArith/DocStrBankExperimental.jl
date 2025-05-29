```
sampdf(Y::DataFrame, k::Union{Int, Vector{Int}}, id = 1:nro(Y); meth = :rand)
```

データフレームの各列からトレーニングセットとテストセットを構築します。

  * `Y` : DataFrame (n, p)。欠損値を含むことがあります。
  * `k` : 各 `Y` 列に対して選択されるテスト観測の数。選択は、考慮される列の非欠損観測の中で行われます。`k` が単一の値の場合、各列に対して同じ数の観測が選択されます。あるいは、`k` は長さ p のベクトルであることもできます。
  * `id` : ID のベクトル (n)。

キーワード引数：

  * `meth` : テストセットのサンプリングの種類。可能な値は次のとおりです： `:rand` = ランダムサンプリング、 `:sys` = 各ソートされた `Y` 列に対する系統的サンプリング（関数 `sampsys` を参照）。

通常、データフレーム `Y` には予測するための応答変数のセットが含まれています。

## 例

```julia
using Jchemo, DataFrames

Y = hcat([rand(5); missing; rand(6)],
   [rand(2); missing; missing; rand(7); missing])
Y = DataFrame(Y, :auto)
n = nro(Y)

k = 3
res = sampdf(Y, k) 
#res = sampdf(Y, k, string.(1:n))
@names res
res.nam
length(res.test)
res.train
res.test

## トレイン/テストの複製分割
rep = 10
k = 3
ids = [sampdf(Y, k) for i = 1:rep]
length(ids)
i = 1    # 複製
ids[i]
ids[i].train 
ids[i].test
j = 1    # 変数 y  
ids[i].train[j]
ids[i].test[j]
ids[i].nam[j]
```
