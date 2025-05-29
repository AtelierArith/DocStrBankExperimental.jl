```
fit!(stat::OnlineStat, y, n)
```

`stat`の「十分統計量」を単一の値の複数の観測で更新します。特別な式が使用されない限り、`fit!(Mean(), 10, 5)`は次のように等価です：

```julia
o = Mean()

for _ in 1:5
    fit!(o, 10)
end
```
