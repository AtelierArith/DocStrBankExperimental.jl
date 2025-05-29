```
conc(v::AbstractVertex, vs::AbstractVertex...; dims, traitdecoration=identity, outwrap=identity)
conc(vname::AbstractString, v::AbstractVertex, vs::AbstractVertex...; dims, traitdecoration=identity, outwrap=identity)
```

次元 `dim` に沿って入力を連結する可変頂点を返します。

`traitdecoration` を使用して、[`named`](@ref)、[`logged`](@ref) または [`validated`](@ref) などの他の特性を付加します。

`outwrap=f` を使用して、連結関数を `f` でラップします。

`conc(vname::AbstractString,...;traitdecoration = f, ...)` は `conc(...;traitdecoration=named(vname) ∘ f, ...)` と同等です。

# 例

```jldoctest
julia> using NaiveNASlib

julia> v = conc(inputvertex.(["in1", "in2", "in3"], 1:3)..., dims=1);

julia> nin(v)
3-element Vector{Int64}:
 1
 2
 3

julia> nout(v)
6

julia> v([1], [2, 3], [4, 5, 6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> v = conc(inputvertex.(["in1", "in2", "in3"], 1:3)..., dims=1, outwrap = f -> (x...) -> 2f(x...));
 
julia> v([1], [2, 3], [4, 5, 6])
6-element Vector{Int64}:
  2
  4
  6
  8
 10
 12
```
