Type-stable axis-specific indexing and identification with a parametric type.

### Type parameters

```julia
struct Axis{name,T}
```

  * `name` : the name of the axis, a Symbol
  * `T` : the type of the axis

### Constructors

```julia
Axis{name}(I)
```

### Arguments

  * `name` : the axis name Symbol or integer dimension
  * `I` : the indexer, any indexing type that the axis supports

### Examples

Here is an example with a Dimensional axis representing a time sequence along rows and a Categorical axis of Symbols for column headers.

```julia
A = AxisArray(reshape(1:60, 12, 5), .1:.1:1.2, [:a, :b, :c, :d, :e])
A[Axis{:col}(2)] # grabs the second column
A[Axis{:col}(:b)] # Same as above, grabs column :b (the second column)
A[Axis{:row}(2)] # grabs the second row
A[Axis{2}(2:5)] # grabs the second through 5th columns
```
