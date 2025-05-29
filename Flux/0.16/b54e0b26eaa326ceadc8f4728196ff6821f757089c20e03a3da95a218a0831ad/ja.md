```
gpu(data::DataLoader)
cpu(data::DataLoader)
```

与えられた `DataLoader` を変換し、イテレートされる際に各データバッチに `gpu` または `cpu` を適用します。（GPU が利用できない場合、これは何もしません。）

# 例

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

大規模なデータセットの場合、`DataLoader` を作成する前にすべてのデータを GPU に移動させるよりも、これが好まれます。次のように：

```julia-repl
julia> Flux.DataLoader((x = ones(2,10), y=2:11) |> gpu, batchsize=3)
4-element DataLoader(::NamedTuple{(:x, :y), Tuple{CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}, UnitRange{Int64}}}, batchsize=3)
  with first element:
  (; x = 2×3 CUDA.CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}, y = 3-element UnitRange{Int64})
```

!!! 警告     これは `gpu` が `DataLoader` に直接適用される場合にのみ機能します。`gpu` は Flux モデルや多くの基本的な Julia 構造体に対して再帰的に作用しますが、（例えば）`DataLoader` のタプルには機能しません。
