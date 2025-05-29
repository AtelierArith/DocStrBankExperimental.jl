`smith_transforms(m::AbstractMatrix{<:Integer})`

`m`のスミス正規形は、`Sᵢ,ᵢ`が`Sⱼ,ⱼ`を割り切るような一意の同値対角行列`S`です（`i≤j`）。整数のユニモジュラー行列`c`と`r`が存在して、`r*m*c==S`が成り立ちます。関数`smith_transforms`は、`.normal=S`、`.rowtrans=r`、および`.coltrans=c`を含む名前付きタプルを返します。

```julia-repl
julia> m=[1 15 28 7;4 5 6 7;7 8 9 7]
3×4 Matrix{Int64}:
 1  15  28  7
 4   5   6  7
 7   8   9  7

julia> n=smith_transforms(m)
(normal = [1 0 0 0; 0 1 0 0; 0 0 3 0], coltrans = [1 0 -1 -84; 0 1 -1 175; 0 0 1 -91; 0 0 0 1], rowtrans = [-2 62 -35; 1 -30 17; -3 97 -55], rank = 3, signdet = nothing)

julia> n.rowtrans*m*n.coltrans==n.normal
true
```
