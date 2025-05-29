```
trace(elems::Vector{<:Element}, b0::AbstractBeam)
```

ビーム `b0` を要素のベクトル `elems` を通してトレースします。ビームのすべての中間状態が記録されます。

戻り値は状態の `Vector` で、最後のエントリが最終ビームです。最終ビームは `propagate(elems, b0)` と同等です。

## 例

```jldoctest
julia> trace([ThinLens(10), FreeSpace(10)], GeometricBeam(w=10.0, k=0.0))
3-element Vector{GeometricBeam{Float64}}:
 GeometricBeam{Float64}(10.0, 0.0, 0.0)
 GeometricBeam{Float64}(10.0, -1.0, 0.0)
 GeometricBeam{Float64}(0.0, -1.0, 10.0)
```
