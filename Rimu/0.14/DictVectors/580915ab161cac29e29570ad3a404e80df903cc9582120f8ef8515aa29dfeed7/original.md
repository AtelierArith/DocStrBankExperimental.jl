```
DVec{K,V,D<:AbstractDict{K,V},S}
```

Dictionary-based vector-like data structure for use with FCIQMC and [KrylovKit](https://github.com/Jutho/KrylovKit.jl). While mostly behaving like a `Dict`, it supports various linear algebra operations such as `norm` and `dot`. It has a [`StochasticStyle`](@ref) that is used to select an appropriate spawning strategy in the FCIQMC algorithm.

See also: [`AbstractDVec`](@ref), [`InitiatorDVec`](@ref), [`PDVec`](@ref).

## Constructors

  * `DVec(dict::AbstractDict[; style, capacity])`: create a `DVec` with `dict` for storage. Note that the data may or may not be copied.
  * `DVec(args...[; style, capacity])`: `args...` are passed to the `Dict` constructor. The `Dict` is used for storage.
  * `DVec{K,V}([; style, capacity])`: create an empty `DVec{K,V}`.
  * `DVec(dv::AbstractDVec[; style, capacity])`: create a `DVec` with the same contents as  `adv`. The `style` is inherited from `dv` by default.

The default `style` is selected based on the `DVec`'s `valtype` (see [`default_style`](@ref)). If a style is given and the `valtype` does not match the `style`'s `eltype`, the values are converted to an appropriate type.

The capacity argument is optional and sets the initial size of the `DVec` via `Base.sizehint!`.

## Examples

```jldoctest
julia> dv = DVec(:a => 1)
DVec{Symbol,Int64} with 1 entry, style = IsStochasticInteger{Int64}()
  :a => 1

julia> dv = DVec(:a => 2, :b => 3; style=IsDeterministic())
DVec{Symbol,Float64} with 2 entries, style = IsDeterministic{Float64}()
  :a => 2.0
  :b => 3.0
```
