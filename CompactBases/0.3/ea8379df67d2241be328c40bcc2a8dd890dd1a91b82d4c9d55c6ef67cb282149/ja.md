```
ExpKnotSet(k, a, b, N[, ml=k, mr=k, base=10, include0=true])
```

`base^a` から `base^b` までの `N` 区間にわたる次数 `k` のノットを構築し、オプションで左端点として 0 を含めることができます。

# 例

```jldoctest
julia> ExpKnotSet(2, -4, 2, 7)
10-element ExpKnotSet{2,2,2,Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}},Array{Float64,1}}:
   0.0
   0.0
   0.0001
   0.001
   0.01
   0.1
   1.0
  10.0
 100.0
 100.0
```
