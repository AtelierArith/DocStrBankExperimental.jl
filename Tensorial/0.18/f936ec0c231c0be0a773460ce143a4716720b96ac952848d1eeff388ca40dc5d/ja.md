```
vol(::AbstractVec{3})
```

ベクトルの体積部分を計算します（主応力とひずみの値を仮定）。これは3Dでのみ利用可能です。

# 例

```jldoctest
julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> vol(x)
3-element Vec{3, Float64}:
 0.3645381733326641
 0.3645381733326641
 0.3645381733326641

julia> vol(x) + dev(x) ≈ x
true
```
