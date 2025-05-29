```
s(N::AbstractUnipartiteNetwork; dims::Union{Nothing,Integer}=nothing)
```

平均加重次数を計算します。これは相互作用の（加重）密度に比例します。

dimsが指定されている場合、入ってくる（`dims=1`）または出ていく（`dims=2`）ものが計算されます。
