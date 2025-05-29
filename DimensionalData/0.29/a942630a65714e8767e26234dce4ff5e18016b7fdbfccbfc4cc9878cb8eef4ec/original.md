```
groupby(A::Union{AbstractDimArray,AbstractDimStack}, dims::Pair...)
groupby(A::Union{AbstractDimArray,AbstractDimStack}, dims::Dimension{<:Callable}...)
```

Group `A` by grouping functions or [`Bins`](@ref) over multiple dimensions.

## Arguments

  * `A`: any `AbstractDimArray` or `AbstractDimStack`.
  * `dims`: `Pair`s such as `groups = groupby(A, :dimname => groupingfunction)` or wrapped [`Dimension`](@ref)s like `groups = groupby(A, DimType(groupingfunction))`. Instead of a grouping function [`Bins`](@ref) can be used to specify group bins.

## Return value

A [`DimGroupByArray`](@ref) is returned, which is basically a regular `AbstractDimArray` but holding the grouped `AbstractDimArray` or `AbstractDimStack`. Its `dims` hold the sorted values returned by the grouping function/s.

Base julia and package methods work on `DimGroupByArray` as for any other `AbstractArray` of `AbstractArray`.

It is common to broadcast or `map` a reducing function over groups, such as `mean` or `sum`, like `mean.(groups)` or `map(mean, groups)`. This will return a regular `DimArray`, or `DimGroupByArray` if `dims` keyword is used in the reducing function or it otherwise returns an `AbstractDimArray` or `AbstractDimStack`.

# Example

Group some data along the time dimension:

```jldoctest groupby; setup = :(using Random; Random.seed!(123))
julia> using DimensionalData, Dates

julia> A = rand(X(1:0.1:20), Y(1:20), Ti(DateTime(2000):Day(3):DateTime(2003)));

julia> groups = groupby(A, Ti => month) # Group by month
┌ 12-element DimGroupByArray{DimArray{Float64,3},1} ┐
├───────────────────────────────────────────────────┴───────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points
├───────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => :Ti=>month
├─────────────────────────────────────────────────────────── group dims ┤
  ↓ X, → Y, ↗ Ti
└───────────────────────────────────────────────────────────────────────┘
  1  191×20×32 DimArray
  2  191×20×28 DimArray
  3  191×20×31 DimArray
  ⋮
 11  191×20×30 DimArray
 12  191×20×31 DimArray
```

And take the mean:

```jldoctest groupby; setup = :(using Statistics)
julia> groupmeans = mean.(groups) # Take the monthly mean
┌ 12-element DimArray{Float64, 1} ┐
├─────────────────────────────────┴─────────────────────────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points
├───────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => :Ti=>month
└───────────────────────────────────────────────────────────────────────┘
  1  0.500064
  2  0.499762
  3  0.500083
  4  0.499985
  ⋮
 10  0.500874
 11  0.498704
 12  0.50047
```

Calculate daily anomalies from the monthly mean. Notice we map a broadcast `.-` rather than `-`. This is because the size of the arrays to not match after application of `mean`.

```jldoctest groupby
julia> map(.-, groupby(A, Ti=>month), mean.(groupby(A, Ti=>month), dims=Ti));
```

Or do something else with Y:

```jldoctest groupby
julia> groupmeans = mean.(groupby(A, Ti=>month, Y=>isodd))
┌ 12×2 DimArray{Float64, 2} ┐
├───────────────────────────┴────────────────────────────────────── dims ┐
  ↓ Ti Sampled{Int64} [1, 2, …, 11, 12] ForwardOrdered Irregular Points,
  → Y  Sampled{Bool} [false, true] ForwardOrdered Irregular Points
├────────────────────────────────────────────────────────────── metadata ┤
  Dict{Symbol, Any} with 1 entry:
  :groupby => (:Ti=>month, :Y=>isodd)
└────────────────────────────────────────────────────────────────────────┘
  ↓ →  false         true
  1        0.499594     0.500533
  2        0.498145     0.501379
  ⋮
 10        0.501105     0.500644
 11        0.498606     0.498801
 12        0.501643     0.499298
```
