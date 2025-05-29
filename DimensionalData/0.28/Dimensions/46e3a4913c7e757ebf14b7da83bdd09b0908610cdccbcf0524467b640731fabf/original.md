```
Dimension
```

Abstract supertype of all dimension types.

Example concrete implementations are [`X`](@ref), [`Y`](@ref), [`Z`](@ref), [`Ti`](@ref) (Time), and the custom [`Dim`](@ref) dimension.

`Dimension`s label the axes of an `AbstractDimArray`, or other dimensional objects, and are used to index into an array.

They may also wrap lookup values for each array axis. This may be any `AbstractVector` matching the array axis length, but will usually be converted to a `Lookup` when use in a constructed object.

A `Lookup` gives more details about the dimension, such as that it is [`Categorical`](@ref) or [`Sampled`](@ref) as [`Points`](@ref) or [`Intervals`](@ref) along some transect. DimensionalData will attempt to guess the lookup from the passed-in index value.

Example:

```jldoctest Dimension
using DimensionalData, Dates

x = X(2:2:10)
y = Y(['a', 'b', 'c'])
ti = Ti(DateTime(2021, 1):Month(1):DateTime(2021, 12))

A = DimArray(zeros(3, 5, 12), (y, x, ti))

# output

╭────────────────────────────╮
│ 3×5×12 DimArray{Float64,3} │
├────────────────────────────┴─────────────────────────────────────────── dims ┐
  ↓ Y  Categorical{Char} ['a', 'b', 'c'] ForwardOrdered,
  → X  Sampled{Int64} 2:2:10 ForwardOrdered Regular Points,
  ↗ Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
[:, :, 1]
 ↓ →   2    4    6    8    10
  'a'  0.0  0.0  0.0  0.0   0.0
  'b'  0.0  0.0  0.0  0.0   0.0
  'c'  0.0  0.0  0.0  0.0   0.0
```

For simplicity, the same `Dimension` types are also used as wrappers in `getindex`, like:

```jldoctest Dimension
x = A[X(2), Y(3)]

# output

╭────────────────────────────────╮
│ 12-element DimArray{Float64,1} │
├────────────────────────────────┴─────────────────────────────────────── dims ┐
  ↓ Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
 2021-01-01T00:00:00  0.0
 2021-02-01T00:00:00  0.0
 2021-03-01T00:00:00  0.0
 2021-04-01T00:00:00  0.0
 2021-05-01T00:00:00  0.0
 2021-06-01T00:00:00  0.0
 2021-07-01T00:00:00  0.0
 2021-08-01T00:00:00  0.0
 2021-09-01T00:00:00  0.0
 2021-10-01T00:00:00  0.0
 2021-11-01T00:00:00  0.0
 2021-12-01T00:00:00  0.0
```

A `Dimension` can also wrap [`Selector`](@ref).

```jldoctest Dimension
x = A[X(Between(3, 4)), Y(At('b'))]

# output

╭──────────────────────────╮
│ 1×12 DimArray{Float64,2} │
├──────────────────────────┴───────────────────────────────────────────── dims ┐
  ↓ X  Sampled{Int64} 4:2:4 ForwardOrdered Regular Points,
  → Ti Sampled{Dates.DateTime} Dates.DateTime("2021-01-01T00:00:00"):Dates.Month(1):Dates.DateTime("2021-12-01T00:00:00") ForwardOrdered Regular Points
└──────────────────────────────────────────────────────────────────────────────┘
 ↓ →   2021-01-01T00:00:00   2021-02-01T00:00:00  …   2021-12-01T00:00:00
 4    0.0                   0.0                      0.0
```
