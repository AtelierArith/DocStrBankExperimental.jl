```
KHist2D(b=300)
```

`b`の中心の近似散布図。 この実装は遅いです！ 代わりに[`IndexedPartition`](@ref)および[`KIndexedPartition`](@ref)を参照してください。

# 例

```
x = randn(10^4)
y = x + randn(10^4)
plot(fit!(KHist2D(), zip(x, y)))
```
