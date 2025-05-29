MVHistoryオブジェクト`tr`に簡単に追加できます。

例：

```julia
using ValueHistories, OnlineStats
v = Variance(BoundedEqualWeight(30))
tr = MVHistory()
for i=1:100
    r = rand()
    fit!(v,r)
    μ,σ = mean(v),std(v)

    # 現在の値を使用して:r、:μ、および:σのエントリを追加します
    @trace tr i r μ σ
end
```
