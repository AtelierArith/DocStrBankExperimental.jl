```
interpolate(BG::BisectionGrid{T, N}) where {T, N}
```

`BG`のすべてのブレッキングエッジに沿った根を、事前に計算された関数評価を使用して線形近似で計算します。`interpolate(linearroot(f), BG)`と同等ですが、各エッジで関数を再評価する必要はありません。

# 例

```jldoctest julia> f(x) = 1 - sum(abs2, x); # 単位円

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);

julia> interpolate(linearroot(f), BG) 8-element Vector{Tuple{Float64, Float64}}:  (1.0, 0.0)  (0.9642857142857143, 0.25)  (0.8571428571428571, 0.5)  (0.75, 0.65)  (0.0, 1.0)  (0.25, 0.9642857142857143)  (0.65, 0.75)  (0.5, 0.8571428571428571)

julia> interpolate(BG) 8-element Vector{Tuple{Float64, Float64}}:  (1.0, 0.0)  (0.9642857142857143, 0.25)  (0.8571428571428571, 0.5)  (0.75, 0.65)  (0.0, 1.0)  (0.25, 0.9642857142857143)  (0.65, 0.75)  (0.5, 0.8571428571428571)
```
