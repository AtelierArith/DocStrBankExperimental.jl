```
ProbMap(T::Type; weight=EqualWeight())
ProbMap(A::AbstractDict{T, Float64}; weight=EqualWeight())
```

ユニークな値をその確率にマッピングする辞書を追跡します。 [`CountMap`](@ref) に似ていますが、重み付けメカニズムを使用します。

# 例

```
o = ProbMap(Int)
fit!(o, rand(1:10, 1000))
probs(o)
```
