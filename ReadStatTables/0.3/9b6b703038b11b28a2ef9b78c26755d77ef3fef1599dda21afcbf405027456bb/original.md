```
LabeledArray{V, N, A<:AbstractArray{V, N}, K} <: AbstractArray{LabeledValue{V, K}, N}
```

`N`-dimensional dense array with elements associated with value labels.

`LabeledArray` provides functionality that is similar to what value labels achieve in statistical software such as Stata. When printed to REPL, a `LabeledArray` just looks like an array of value labels. Yet, only the underlying values of type `V` are stored in an array of type `A`. The associated value labels are looked up from a dictionary of type `Dict{K, String}`. If a value `v` is not equal (`==`) to a key in the dictionary, then `string(v)` is taken as the value label. The elements of type [`LabeledValue{V, K}`](@ref) are only constructed lazily when they are retrieved.

The array of values underlying a `LabeledArray` can be accessed via [`refarray`](@ref). The dictionary of value labels assoicated with a `LabeledArray` can be accessed via [`getvaluelabels`](@ref). An iterator over the value labels for each element, which has the same array shape as the `LabeledArray`, can be obtained via [`valuelabels`](@ref).

Equality comparison (`==`) involving a `LabeledArray` only compares the underlying values and disregard any value label. To compare the value labels, use [`valuelabels`](@ref) to obtain the labels first.

Additional array methods such as `push!`, `insert!`, `deleteat!`, `append!` are supported for [`LabeledVector`](@ref). They are applied on the underlying array of values retrieved via [`refarray`](@ref) and do not modify the dictionary of value labels.

For convenience, `LabeledArray(x::AbstractArray{<:AbstractString}, ::Type{T}=Int32)` converts a string array to a `LabeledArray` by encoding the string values with integers of the specified type (`Int32` by default).

# Examples

```jldoctest
julia> lbls1 = Dict(1=>"a", 2=>"b");

julia> lbls2 = Dict(1.0=>"p", 2.0=>"q");

julia> x = LabeledArray([0, 1, 2], lbls1)
3-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b

julia> y = LabeledArray([0.0, 1.0, 2.0], lbls2)
3-element LabeledVector{Float64, Vector{Float64}, Float64}:
 0.0 => 0.0
 1.0 => p
 2.0 => q

julia> x == y
true

julia> x == 0:2
true

julia> refarray(x)
3-element Vector{Int64}:
 0
 1
 2

julia> getvaluelabels(x)
Dict{Int64, String} with 2 entries:
  2 => "b"
  1 => "a"

julia> valuelabels(x) == ["0", "a", "b"]
true

julia> push!(x, 2)
4-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 2 => b

julia> push!(x, 3 => "c")
5-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 2 => b
 3 => c

julia> deleteat!(x, 4:5)
3-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b

julia> append!(x, [0, 1, 2])
6-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 0 => 0
 1 => a
 2 => b

julia> v = ["a", "b", "c"];

julia> LabeledArray(v, Int16)
3-element LabeledVector{Int16, Vector{Int16}, Union{Char, Int32}}:
 1 => a
 2 => b
 3 => c
```
