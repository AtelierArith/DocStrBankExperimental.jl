```julia
algorithm(pp)

```

`pp`の人パラメータを計算するために使用されるアルゴリズムを取得します。

## 例

```jldoctest
julia> pp = person_parameters(OnePL, fill(zeros(3), 5), zeros(3), MLE());

julia> algorithm(pp)
MLE{Roots.Secant}(Roots.Secant())
```
