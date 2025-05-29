```
@def_sde_system ex
```

where `ex` is the expression to define to define a new AbstractSDESystem component type. The usage is as follows:

```julia
@def_sde_system mutable struct MySDESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractSDESystem
    param1::T1 = param1_default                 # optional field 
    param2::T2 = param2_default                 # optional field 
    param3::T3 = param3_default                 # optional field
        ⋮
    paramN::TN = paramN_default                 # optional field 
    drift::DR = drift_function                  # mandatory field
    diffusion::DF = diffusion_function          # mandatory field
    readout::RO = readout_functtion             # mandatory field
    state::ST = state_default                   # mandatory field
    input::IP = input_default                   # mandatory field
    output::OP = output_default                 # mandatory field
end
```

Here, `MySDESystem` has `N` parameters. `MySDESystem` is represented by the `drift`, `diffusion` and `readout` function. `state`, `input` and `output` is the initial state, input port and output port of `MySDESystem`.

!!! warning
    `drift` must have the signature 

    ```julia
    function drift((dx, x, u, t, args...; kwargs...)
        dx .= .... # update dx
    end
    ```

    and `diffusion` must have the signature 

    ```julia
    function diffusion((dx, x, u, t, args...; kwargs...)
        dx .= .... # update dx
    end
    ```

    and `readout` must have the signature 

    ```julia
    function readout(x, u, t)
        y = ...
        return y
    end
    ```


!!! warning
    New SDE system must be a subtype of `AbstractSDESystem` to function properly.


# Example

```julia
julia> @def_sde_system mutable struct MySDESystem{DR, DF, RO, IP, OP} <: AbstractSDESystem
           η::Float64 = 1.
           drift::DR = (dx, x, u, t) -> (dx .= x)
           diffusion::DF = (dx, x, u, t, η=η) -> (dx .= η)
           readout::RO = (x, u, t) -> x 
           state::Vector{Float64} = rand(2) 
           input::IP = nothing 
           output::OP = Outport(2)
       end

julia> ds = MySDESystem();
```
