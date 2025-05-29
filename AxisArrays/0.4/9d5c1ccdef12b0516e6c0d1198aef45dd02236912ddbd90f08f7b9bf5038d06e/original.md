An AxisArray is an AbstractArray that wraps another AbstractArray and adds axis names and values to each array dimension. AxisArrays can be indexed by using the named axes as an alternative to positional indexing by dimension. Other advanced indexing along axis values are also provided.

### Type parameters

The AxisArray contains several type parameters:

```julia
struct AxisArray{T,N,D,Ax} <: AbstractArray{T,N}
```

  * `T` : the elemental type of the AbstractArray
  * `N` : the number of dimensions
  * `D` : the type of the wrapped AbstractArray
  * `Ax` : the names and types of the axes, as a (specialized) NTuple{N, Axis}

### Constructors

```julia
AxisArray(A::AbstractArray, axes::Axis...)
AxisArray(A::AbstractArray, names::Symbol...)
AxisArray(A::AbstractArray, vectors::AbstractVector...)
AxisArray(A::AbstractArray, (names...,), (steps...,), [(offsets...,)])
```

### Arguments

  * `A::AbstractArray` : the wrapped array data
  * `axes` or `names` or `vectors` : dimensional information for the wrapped array

The dimensional information may be passed in one of three ways and is entirely optional. When the axis name or value is missing for a dimension, a default is substituted. The default axis names for dimensions `(1, 2, 3, 4, 5, ...)` are `(:row, :col, :page, :dim_4, :dim_5, ...)`. The default axis values are `Base.axes(A, d)` for each missing dimension `d`.

### Indexing

Indexing returns a view into the original data. The returned view is a new AxisArray that wraps a SubArray. Indexing should be type stable. Use `Axis{axisname}(idx)` to index based on a specific axis. `axisname` is a Symbol specifying the axis to index/slice, and `idx` is a normal indexing object (`Int`, `Array{Int,1}`, etc.) or a custom indexing type for that particular type of axis.

Two main types of axes supported by default include:

  * Categorical axis – These are vectors of labels, normally Symbols or strings. Elements or slices can be indexed by elements or vectors of elements.
  * Dimensional axis – These are sorted vectors or iterators that can be indexed by `ClosedInterval()`. These are commonly used for sequences of times or date-times. For regular sample rates, ranges can be used.

User-defined axis types can be added along with custom indexing behaviors. To add add a custom type as a Categorical or Dimensional axis, add a trait using [`AxisArrays.axistrait`](@ref).

For more advanced indexing, you can define custom methods for [`AxisArrays.axisindexes`](@ref).

### Examples

Here is an example with a Dimensional axis representing a time sequence along rows (it's a FloatRange) and a Categorical axis of Symbols for column headers.

```julia
A = AxisArray(reshape(1:15, 5, 3), Axis{:time}(.1:.1:0.5), Axis{:col}([:a, :b, :c]))
A[Axis{:time}(1:3)]   # equivalent to A[1:3,:]
A[Axis{:time}(ClosedInterval(.2,.4))] # restrict the AxisArray along the time axis
A[ClosedInterval(0.,.3), [:a, :c]]   # select an interval and two columns
```
