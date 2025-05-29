```
cut(x::AbstractArray, breaks::AbstractVector;
    labels::Union{AbstractVector,Function},
    extend::Union{Bool,Missing}=false, allowempty::Bool=false)
```

Cut a numeric array into intervals at values `breaks` and return an ordered `CategoricalArray` indicating the interval into which each entry falls. Intervals are of the form `[lower, upper)`, i.e. the lower bound is included and the upper bound is excluded, except if `extend=true` the last interval, which is then closed on both ends, i.e. `[lower, upper]`.

If `x` accepts missing values (i.e. `eltype(x) >: Missing`) the returned array will also accept them.

# Keyword arguments

  * `extend::Union{Bool, Missing}=false`: when `false`, an error is raised if some values in `x` fall outside of the breaks; when `true`, breaks are automatically added to include all values in `x`, and the upper bound is included in the last interval; when `missing`, values outside of the breaks generate `missing` entries.
  * `labels::Union{AbstractVector, Function}`: a vector of strings, characters or numbers giving the names to use for the intervals; or a function `f(from, to, i; leftclosed, rightclosed)` that generates the labels from the left and right interval boundaries and the group index. Defaults to `"[from, to)"` (or `"[from, to]"` for the rightmost interval if `extend == true`).
  * `allowempty::Bool=false`: when `false`, an error is raised if some breaks appear multiple times, generating empty intervals; when `true`, duplicate breaks are allowed and the intervals they generate are kept as unused levels (but duplicate labels are not allowed).

# Examples

```jldoctest
julia> using CategoricalArrays

julia> cut(-1:0.5:1, [0, 1], extend=true)
5-element CategoricalArray{String,1,UInt32}:
 "[-1.0, 0.0)"
 "[-1.0, 0.0)"
 "[0.0, 1.0]"
 "[0.0, 1.0]"
 "[0.0, 1.0]" 

julia> cut(-1:0.5:1, 2)
5-element CategoricalArray{String,1,UInt32}:
 "Q1: [-1.0, 0.0)"
 "Q1: [-1.0, 0.0)"
 "Q2: [0.0, 1.0]"
 "Q2: [0.0, 1.0]"
 "Q2: [0.0, 1.0]" 

julia> cut(-1:0.5:1, 2, labels=["A", "B"])
5-element CategoricalArray{String,1,UInt32}:
 "A"
 "A"
 "B"
 "B"
 "B" 

julia> cut(-1:0.5:1, 2, labels=[-0.5, +0.5])
5-element CategoricalArray{Float64,1,UInt32}:
 -0.5
 -0.5
 0.5
 0.5
 0.5

julia> fmt(from, to, i; leftclosed, rightclosed) = "grp $i ($from//$to)"
fmt (generic function with 1 method)

julia> cut(-1:0.5:1, 3, labels=fmt)
5-element CategoricalArray{String,1,UInt32}:
 "grp 1 (-1.0//-0.3333333333333335)"
 "grp 1 (-1.0//-0.3333333333333335)"
 "grp 2 (-0.3333333333333335//0.33333333333333326)"
 "grp 3 (0.33333333333333326//1.0)"
 "grp 3 (0.33333333333333326//1.0)"
```
