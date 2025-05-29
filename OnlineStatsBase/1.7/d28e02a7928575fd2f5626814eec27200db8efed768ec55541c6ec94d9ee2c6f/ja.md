```
FilterTransform(stat::OnlineStat{S}, T = S; filter = x->true, transform = identity)
FilterTransform(T => filter => transform => stat)
```

OnlineStatをラップし、その入力をフィルタリングおよび変換します。変換に応じて、単一の観測値の型（`T`）を指定する必要がある場合があります。

# 例

```
o = FilterTransform(Mean(), Union{Missing,Number}, filter=!ismissing)
fit!(o, [1, missing, 3])

o = FilterTransform(String => (x->true) => (x->parse(Int,x)) => Mean())
fit!(o, "1")
```
