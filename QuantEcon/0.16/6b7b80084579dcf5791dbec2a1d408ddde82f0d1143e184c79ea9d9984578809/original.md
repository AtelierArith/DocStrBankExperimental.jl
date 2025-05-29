```julia
@def_sim sim_name default_type_params begin
    obs_typedef
end
```

Given a type definition for a single observation in a simulation (`obs_typedef`), evaluate that type definition as is, but also creates a second type named `sim_name` as well as various methods on the new type.

The fields of `sim_name` will have the same name as the fields of `obs_typedef`, but will be arrays of whatever the type of the corresponding `obs_typedef` field was. The intention is for `sim_name` to be a struct of arrays (see https://en.wikipedia.org/wiki/AOS*and*SOA). If you want an array of structs, just simply collect an array of instances of the type defined in `obs_typedef`. The struct of arrays storage format has better cache efficiency and data locality if you want to operate on all values of a particular field at once, rather than all the fields of a particular value.

In addition to the new type `sim_name`, the following methods will be defined:

  * `sim_name(sz::NTuple{N,Int})`. This is a constructor for `sim_name` that allocates arrays of size `sz` for each field. If `obs_typedef` inlcuded any type parameters, then the default values (specified in `default_type_params`) will be used.
  * `Base.endof(::sim_name)`: equal to the length of any of its fields
  * `Base.length(::sim_name)`: equal to the length of any of its fields
  * The iterator protocol for `sim_name`. The type of each element of the iterator is the type defined in `obs_typedef`. This amounts tho defining the following methods

      * `Base.start(::sim_name)::Int`
      * `Base.next(::sim_name, ::Int)::Tuple{Observation,Int}`
      * `Base.done(::sim_name, ::Int)::Bool`
  * `Base.getindex(sim::sim_name, ix::Int)`. This implements *linear indexing* for `sim_name` and will return an instance of the type defined in `obs_typedef`

## Example

NOTE: the `using MacroTools`  and call to `MacroTools.prettify` is not necessary and is only used here to clean up the output so it is easier to read

```
julia> using MacroTools

julia> macroexpand(:(@def_sim Simulation (T => Float64,) struct Observation{T<:Number}
           c::T
           k::T
           i_z::Int
       end
       )) |> MacroTools.prettify
quote
    struct Simulation{prairiedog, T <: Number}
        c::Array{T, prairiedog}
        k::Array{T, prairiedog}
        i_z::Array{Int, prairiedog}
    end
    function Simulation{prairiedog}(sz::NTuple{prairiedog, Int})
        c = Array{Float64, prairiedog}(sz)
        k = Array{Float64, prairiedog}(sz)
        i_z = Array{Int, prairiedog}(sz)
        Simulation(c, k, i_z)
    end
    struct Observation{T <: Number}
        c::T
        k::T
        i_z::Int
    end
    Base.endof(sim::Simulation) = length(sim.c)
    Base.length(sim::Simulation) = endof(sim)
    Base.start(sim::Simulation) = 1
    Base.next(sim::Simulation, ix::Int) = (sim[ix], ix + 1)
    Base.done(sim::Simulation, ix::Int) = ix >= length(sim)
    function Base.getindex(sim::Simulation, ix::Int)
        $(Expr(:boundscheck, true))
        if ix > length(sim)
            throw(BoundsError("$(length(sim))-element Simulation at index $(ix)"))
        end
        $(Expr(:boundscheck, :pop))
        $(Expr(:inbounds, true))
        out = Observation(sim.c[ix], sim.k[ix], sim.i_z[ix])
        $(Expr(:inbounds, :pop))
        return out
    end
end
```
