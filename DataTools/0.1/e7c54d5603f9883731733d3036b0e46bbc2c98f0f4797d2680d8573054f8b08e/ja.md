```
meanvar
```

平均と分散を計算するための縮小関数。

# 例

```jldoctest
julia> using DataTools, Transducers, Statistics

julia> acc = foldl(meanvar, Filter(isodd), 1:96)
MeanVarState(mean=48.0, var=784.0, count=48)

julia> acc.mean, mean(acc)
(48.0, 48.0)

julia> acc.var, var(acc), var(acc, corrected = false)
(784.0, 784.0, 767.6666666666666)

julia> acc.std, std(acc)
(28.0, 28.0)

julia> acc.count
48

julia> m, v, c = acc;  # デストラクチャリングは機能します

julia> Tuple(acc)  # (mean, var, count)
(48.0, 784.0, 48)

julia> NamedTuple(acc)
(mean = 48.0, var = 784.0, count = 48)

julia> rf = oncol(a = meanvar, b = meanvar);

julia> foldl(rf, Map(identity), [(a = 1, b = 2), (a = 2, b = 3)])
(a = MeanVarState(mean=1.5, var=0.5, count=2), b = MeanVarState(mean=2.5, var=0.5, count=2))
```
