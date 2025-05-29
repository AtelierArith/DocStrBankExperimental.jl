```julia
modeltype(pp)

```

`pp`の人パラメータを計算するために使用されるスケーリングモデルを取得します。

## 例

```jldoctest
julia> pp = person_parameters(TwoPL, fill(zeros(3), 10), fill((a = 1.0, b = 0.0), 3), WLE());

julia> modeltype(pp)
TwoParameterLogisticModel
```
