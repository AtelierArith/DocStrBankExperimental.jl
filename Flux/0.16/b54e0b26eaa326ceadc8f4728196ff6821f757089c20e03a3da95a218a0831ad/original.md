```
gpu(data::DataLoader)
cpu(data::DataLoader)
```

Transforms a given `DataLoader` to apply `gpu` or `cpu` to each batch of data, when iterated over. (If no GPU is available, this does nothing.)

# Example

```julia-repl
julia> dl = Flux.DataLoader((x = ones(2,10), y='a':'j'), batchsize=3)
4-element DataLoader(::NamedTuple{(:x, :y), Tuple{Matrix{Float64}, StepRange{Char, Int64}}}, batchsize=3)
  with first element:
  (; x = 2×3 Matrix{Float64}, y = 3-element StepRange{Char, Int64})

julia> first(dl)
(x = [1.0 1.0 1.0; 1.0 1.0 1.0], y = 'a':1:'c')

julia> c_dl = gpu(dl)
4-element DataLoader(::MLUtils.MappedData{:auto, typeof(gpu), NamedTuple{(:x, :y), Tuple{Matrix{Float64}, StepRange{Char, Int64}}}}, batchsize=3)
  with first element:
  (; x = 2×3 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}, y = 3-element StepRange{Char, Int64})

julia> first(c_dl).x
2×3 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0  1.0
 1.0  1.0  1.0
```

For large datasets, this is preferred over moving all the data to the GPU before creating the `DataLoader`, like this:

```julia-repl
julia> Flux.DataLoader((x = ones(2,10), y=2:11) |> gpu, batchsize=3)
4-element DataLoader(::NamedTuple{(:x, :y), Tuple{CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}, UnitRange{Int64}}}, batchsize=3)
  with first element:
  (; x = 2×3 CUDA.CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}, y = 3-element UnitRange{Int64})
```

!!! warning
    This only works if `gpu` is applied directly to the `DataLoader`. While `gpu` acts recursively on Flux models and many basic Julia structs, it will not work on (say) a tuple of `DataLoader`s.

