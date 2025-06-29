```
@def_rode_system ex
```

where `ex` is the expression to define to define a new AbstractRODESystem component type. The usage is as follows:

```julia
@def_rode_system mutable struct MyRODESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractRODESystem
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

Here, `MyRODESystem` has `N` parameters. `MyRODESystem` is represented by the `righthandside` and `readout` function. `state`, `input` and `output` is the initial state, input port and output port of `MyRODESystem`.

!!! warning
    `righthandside` must have the signature 

    ```julia
    function righthandside((dx, x, u, t, W, args...; kwargs...)
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
    New RODE system must be a subtype of `AbstractRODESystem` to function properly.


# Example

```julia
julia> @def_rode_system mutable struct MySystem{RH, RO, IP, OP} <: AbstractRODESystem
           A::Matrix{Float64} = [2. 0.; 0 -2]
           righthandside::RH = (dx, x, u, t, W) -> (dx .= A * x * W)
           readout::RO = (x, u, t) -> x 
           state::Vector{Float64} = rand(2) 
           input::IP = nothing 
           output::OP = Outport(2)
       end

julia> ds = MySystem();
```
