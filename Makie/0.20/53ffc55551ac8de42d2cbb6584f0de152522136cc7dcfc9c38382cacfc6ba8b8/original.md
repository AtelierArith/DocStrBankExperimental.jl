spy(x::Range, y::Range, z::AbstractSparseArray)

Visualizes big sparse matrices. Usage:

```julia
N = 200_000
x = sprand(Float64, N, N, (3(10^6)) / (N*N));
spy(x)
# or if you want to specify the range of x and y:
spy(0..1, 0..1, x)
```

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.spy}` are: 

```
  colormap     :viridis
  colorrange   MakieCore.Automatic()
  colorscale   identity
  framecolor   :black
  framesize    1
  inspectable  true
  marker       MakieCore.Automatic()
  markersize   MakieCore.Automatic()
  visible      true
```
