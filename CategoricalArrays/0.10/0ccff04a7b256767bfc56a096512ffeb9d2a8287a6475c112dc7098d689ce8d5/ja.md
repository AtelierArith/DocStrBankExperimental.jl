```
recode!(a::AbstractArray[, default::Any], pairs::Pair...)
```

インプレースでの再コーディングのための便利な関数で、`recode!(a, a, ...)`と同等です。

# 例

```jldoctest
julia> using CategoricalArrays

julia> x = collect(1:10);

julia> recode!(x, 1=>100, 2:4=>0, [5; 9:10]=>-1);

julia> x
10-element Vector{Int64}:
 100
   0
   0
   0
  -1
   6
   7
   8
  -1
  -1
```
