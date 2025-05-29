```
PDVec{K,V}(; kwargs...)
PDVec(iter; kwargs...)
PDVec(pairs...; kwargs...)
```

Dictionary-based vector-like data structure for use with FCIQMC and [KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl). While mostly behaving like a `Dict`, it supports various linear algebra operations such as `norm` and `dot`, and the interface defined in [VectorInterface](https://github.com/Jutho/VectorInterface.jl).

The P in `PDVec` stands for parallel. `PDVec`s perform `mapreduce`, `foreach`, and various linear algebra operations in a threaded manner. If MPI is available, these operations are automatically distributed as well. As such it is not recommended to iterate over `pairs`, `keys`, or `values` directly unless explicitly performing them on the [`localpart`](@ref) of the vector.

See also: [`AbstractDVec`](@ref), [`DVec`](@ref), [`InitiatorDVec`](@ref).

## Keyword arguments

  * `style =`[`default_style`](@ref)`(V)`: A [`StochasticStyle`](@ref) that is used to select the spawning strategy in the FCIQMC algorithm.
  * `initiator =`[`NonInitiator`](@ref)`()`: An [`InitiatorRule`](@ref), used in FCIQMC to remove the sign problem.
  * `communicator`: A [`Communicator`](@ref) that controls how operations are performed when using MPI. The defaults are [`NotDistributed`](@ref) when not using MPI and [`AllToAll`](@ref) when using MPI.

# Extended Help

## Segmentation

The vector is split into `Threads.nthreads()` subdictionaries called segments. Which dictionary a key-value pair is mapped to is determined by the hash of the key. The purpose of this segmentation is to allow parallel processing - functions such as `mapreduce`, `add!` or `dot` (full list below) process each subdictionary on a separate thread.

See also [`PDWorkingMemory`](@ref).

### Example

```julia
julia> add = FermiFS2C((1,1,0,0), (0,0,1,1));

julia> op = HubbardMom1D(add; t=4/π^2, u=4);

julia> pv = PDVec(add => 1.0)
1-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↑↓↓⟩" => 1.0

julia> pv = op * pv
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => 1.0
  fs"|↑↑↓↓⟩" => 4.0
  fs"|↓↑↓↑⟩" => 1.0
  fs"|↓↑↑↓⟩" => -1.0
  fs"|⇅⋅⋅⇅⟩" => 1.0
  fs"|↑↓↓↑⟩" => -1.0
  fs"|⋅⇅⇅⋅⟩" => 1.0

julia> scale!(pv, -1); pv
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => -1.0
  fs"|↑↑↓↓⟩" => -4.0
  fs"|↓↑↓↑⟩" => -1.0
  fs"|↓↑↑↓⟩" => 1.0
  fs"|⇅⋅⋅⇅⟩" => -1.0
  fs"|↑↓↓↑⟩" => 1.0
  fs"|⋅⇅⇅⋅⟩" => -1.0

julia> dest = similar(pv)
0-element PDVec: style = IsDeterministic{Float64}()

julia> map!(x -> x + 2, dest, values(pv))
7-element PDVec: style = IsDeterministic{Float64}()
  fs"|↑↓↑↓⟩" => 1.0
  fs"|↑↑↓↓⟩" => -2.0
  fs"|↓↑↓↑⟩" => 1.0
  fs"|↓↑↑↓⟩" => 3.0
  fs"|⇅⋅⋅⇅⟩" => 1.0
  fs"|↑↓↓↑⟩" => 3.0
  fs"|⋅⇅⇅⋅⟩" => 1.0

julia> sum(values(pv))
-6.0

julia> dot(dest, pv)
10.0

julia> dot(dest, op, pv)
44.0
```

## MPI

When MPI is active, all parallel reductions are automatically reduced across MPI ranks with a call to `MPI.Allreduce!`.

In a distributed setting, `PDVec` does not support iteration without first making it explicit the iteration is only to be performed on the local segments of the vector. This is done with [`localpart`](@ref). In general, even when not using MPI, it is best practice to use [`localpart`](@ref) when explicit iteration is required.

## Use with KrylovKit

`PDVec` is compatible with `eigsolve` from [KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl). When used, the diagonalisation is performed in a threaded and distributed manner. Using multiple MPI ranks with this method does not distribute the memory load effectively, but does result in significant speedups.

### Example

```julia
julia> using KrylovKit

julia> add = BoseFS((0,0,5,0,0));

julia> op = HubbardMom1D(add; u=6.0);

julia> pv = PDVec(add => 1.0);

julia> results = eigsolve(op, pv, 4, :SR);

julia> results[1][1:4]
4-element Vector{Float64}:
 -3.4311156892322234
  1.1821748602612363
  3.7377753753082823
  6.996390417443125
```

## Parallel functionality

The following functions are threaded and MPI-compatible:

  * From Base: `mapreduce` and derivatives (`sum`, `prod`, `reduce`...), `all`, `any`,`map!` (on `values` only), `+`, `-`, `*`
  * From LinearAlgebra: `rmul!`, `lmul!`, `mul!`, `axpy!`, `axpby!`, `dot`, `norm`, `normalize`, `normalize!`
  * The full interface defined in [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl)
