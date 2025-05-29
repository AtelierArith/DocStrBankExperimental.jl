```julia
yq = linterp1s(x::AbstractArray, y::AbstractArray, xq; extrapolate=:Linear)
```

`linterp1`（1次元の単純線形補間）と同様ですが、`x`がすでに昇順にソートされていない場合は、ノット`x`と値`y`をペアでソートします。

### 例

```julia
julia> linterp1s(10:-1:1, 1:10, 5.5)
5.5

julia> linterp1s(10:-1:1, 1:10, 0.5:10.5)
11-element Vector{Float64}:
 10.5
  9.5
  8.5
  7.5
  6.5
  5.5
  4.5
  3.5
  2.5
  1.5
  0.5
```
