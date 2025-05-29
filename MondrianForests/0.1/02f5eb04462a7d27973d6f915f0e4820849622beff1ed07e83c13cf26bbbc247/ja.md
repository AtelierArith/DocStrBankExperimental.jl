```
MondrianTree(id::String, lambda::Float64, lower::NTuple{d,Float64},
             upper::NTuple{d,Float64}, creation_time::Float64) where {d}
```

指定されたid、寿命、下限および上限のセル座標、作成時間を持つMondrianツリーをサンプリングします。内部構築メソッドで使用されます。

# 例

```julia
id = ""
lambda = 3.0
lower = ntuple(i -> 0.2, d)
upper = ntuple(i -> 0.7, d)
creation_time = 0.0
tree = MondrianTree(id, lambda, lower, upper, creation_time)
```
