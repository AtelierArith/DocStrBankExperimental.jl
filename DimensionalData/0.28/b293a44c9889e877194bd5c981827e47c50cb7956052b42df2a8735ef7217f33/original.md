```
DimArray <: AbstractDimArray

DimArray(data, dims, refdims, name, metadata)
DimArray(data, dims::Tuple; refdims=(), name=NoName(), metadata=NoMetadata())
```

The main concrete subtype of [`AbstractDimArray`](@ref).

`DimArray` maintains and updates its `Dimension`s through transformations and moves dimensions to reference dimension `refdims` after reducing operations (like e.g. `mean`).

## Arguments

  * `data`: An `AbstractArray`.
  * `dims`: A `Tuple` of `Dimension`
  * `name`: A string name for the array. Shows in plots and tables.
  * `refdims`: refence dimensions. Usually set programmatically to track past   slices and reductions of dimension for labelling and reconstruction.
  * `metadata`: `Dict` or `Metadata` object, or `NoMetadata()`

Indexing can be done with all regular indices, or with [`Dimension`](@ref)s and/or [`Selector`](@ref)s. 

Indexing `AbstractDimArray` with non-range `AbstractArray` has undefined effects on the `Dimension` index. Use forward-ordered arrays only"

Example:

```jldoctest; setup = :(using Random; Random.seed!(123))
julia> using Dates, DimensionalData

julia> ti = Ti(DateTime(2001):Month(1):DateTime(2001,12));

julia> x = X(10:10:100);

julia> A = DimArray(rand(12,10), (ti, x), name="example");

julia> A[X(Near([12, 35])), Ti(At(DateTime(2001,5)))]
╭───────────────────────────────────────╮
│ 2-element DimArray{Float64,1} example │
├───────────────────────────────────────┴─────────────── dims ┐
  ↓ X Sampled{Int64} [10, 40] ForwardOrdered Irregular Points
└─────────────────────────────────────────────────────────────┘
 10  0.253849
 40  0.637077

julia> A[Near(DateTime(2001, 5, 4)), Between(20, 50)]
╭───────────────────────────────────────╮
│ 4-element DimArray{Float64,1} example │
├───────────────────────────────────────┴───────────── dims ┐
  ↓ X Sampled{Int64} 20:10:50 ForwardOrdered Regular Points
└───────────────────────────────────────────────────────────┘
 20  0.774092
 30  0.823656
 40  0.637077
 50  0.692235
```
