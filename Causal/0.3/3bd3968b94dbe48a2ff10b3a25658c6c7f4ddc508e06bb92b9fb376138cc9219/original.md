```
@def_discrete_system ex
```

where `ex` is the expression to define to define a new AbstractDiscreteSystem component type. The usage is as follows:

```julia
@def_discrete_system mutable struct MyDiscreteSystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractDiscreteSystem
    param1::T1 = param1_default                 # optional field 
    param2::T2 = param2_default                 # optional field 
    param3::T3 = param3_default                 # optional field
        ⋮
    paramN::TN = paramN_default                 # optional field 
    righthandside::RH = righthandside_function  # mandatory field
    readout::RO = readout_function              # mandatory field
    state::ST = state_default                   # mandatory field
    input::IP = input_default                   # mandatory field
    output::OP = output_default                 # mandatory field 
end
```

Here, `MyDiscreteSystem` has `N` parameters. `MyDiscreteSystem` is represented by the `righthandside` and `readout` function. `state`, `input` and `output` is the state, input port and output port of `MyDiscreteSystem`.

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
    New discrete system must be a subtype of `AbstractDiscreteSystem` to function properly.


# Example

```julia
julia> @def_discrete_system mutable struct MyDiscreteSystem{RH, RO, IP, OP} <: AbstractDiscreteSystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       righthandside::RH = (dx, x, u, t, α=α) -> (dx[1] = α * x[1] + u[1](t))
       state::Vector{Float64} = [1.]
       readout::RO = (x, u, t) -> x
       input::IP = Inport(1) 
       output::OP = Outport(1) 
       end

julia> ds = MyDiscreteSystem();

julia> ds.input 
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
