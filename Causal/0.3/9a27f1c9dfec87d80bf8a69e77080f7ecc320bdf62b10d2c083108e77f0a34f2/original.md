```
@def_ode_system ex
```

where `ex` is the expression to define to define a new AbstractODESystem component type. The usage is as follows:

```julia
@def_ode_system mutable struct MyODESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractODESystem
    param1::T1 = param1_default                     # optional field 
    param2::T2 = param2_default                     # optional field 
    param3::T3 = param3_default                     # optional field
        ⋮
    paramN::TN = paramN_default                     # optional field 
    righthandside::RH = righthandeside_function     # mandatory field
    readout::RO = readout_function                  # mandatory field
    state::ST = state_default                       # mandatory field
    input::IP = input_default                       # mandatory field
    output::OP = output_default                     # mandatory field 
end
```

Here, `MyODESystem` has `N` parameters. `MyODESystem` is represented by the `righthandside` and `readout` function. `state`, `input` and `output` is the state, input port and output port of `MyODESystem`.

!!! warning
    `righthandside` must have the signature 

    ```julia
    function righthandside(dx, x, u, t, args...; kwargs...)
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
    New ODE system must be a subtype of `AbstractODESystem` to function properly.


!!! warning
    New ODE system must be mutable type.


# Example

```julia
julia> @def_ode_system mutable struct MyODESystem{RH, RO, IP, OP} <: AbstractODESystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       righthandside::RH = (dx, x, u, t, α=α) -> (dx[1] = α * x[1] + u[1](t))
       readout::RO = (x, u, t) -> x
       state::Vector{Float64} = [1.]
       input::IP = Inport(1) 
       output::OP = Outport(1) 
       end

julia> ds = MyODESystem();

julia> ds.input 
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
