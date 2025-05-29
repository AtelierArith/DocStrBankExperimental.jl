便利なマクロで、コードを[`Marker.startregion`](@ref)と[`Marker.stopregion`](@ref)で囲みます。

# 例

```julia
julia> using LIKWID

julia> Marker.init()

julia> @marker "sleeping..." sleep(1)
true

julia> @marker "create rand vec" rand(100)
true

julia> Marker.close()

```
