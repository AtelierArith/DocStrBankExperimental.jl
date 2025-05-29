```
convexity(yield,cfs,times)
convexity(yield,valuation_function)
```

コンベクシティを計算します。     - `yield` は固定の有効利回りである必要があります（例： `0.05`）。     - `times` は省略可能で、`cfs` が最初の期間の終わりから均等に間隔を置いていると仮定します。

# 例

キャッシュフローと時間のベクトルを使用する

```julia-repl
julia> times = 1:5
julia> cfs = [0,0,0,0,100]
julia> duration(0.03,cfs,times)
4.854368932038834
julia> duration(Macaulay(),0.03,cfs,times)
5.0
julia> duration(Modified(),0.03,cfs,times)
4.854368932038835
julia> convexity(0.03,cfs,times)
28.277877274012614

```

任意の値関数を使用する: 

```julia-repl
julia> lump_sum_value(amount,years,i) = amount / (1 + i ) ^ years
julia> my_lump_sum_value(i) = lump_sum_value(100,5,i)
julia> duration(0.03,my_lump_sum_value)
4.854368932038835
julia> convexity(0.03,my_lump_sum_value)
28.277877274012617

```
