```
@def_dae_system ex
```

where `ex` is the expression to define to define a new AbstractDAESystem component type. The usage is as follows:

```julia
@def_dae_system mutable struct MyDAESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractDAESystem
    param1::T1 = param1_default                 # optional field 
    param2::T2 = param2_default                 # optional field 
    param3::T3 = param3_default                 # optional field
        ⋮
    paramN::TN = paramN_default                 # optional field 
    righthandside::RH = righthandside_function  # mandatory field
    readout::RO = readout_function              # mandatory field
    state::ST = state_default                   # mandatory field
    stateder::ST = stateder_default             # mandatory field
    diffvars::Vector{Bool} = diffvars_default   # mandatory field
    input::IP = input_default                   # mandatory field
    output::OP = output_default                 # mandatory field
end
```

Here, `MyDAESystem` has `N` parameters. `MyDAESystem` is represented by the `righthandside` and `readout` function. `state`, 'stateder`,`diffvars`,`input`and`output`is the initial state, initial value of differential variables, vector signifing differetial variables, input port and output port of`MyDAESystem`.

!!! warning
    `righthandside` must have the signature 

    ```julia
    function righthandside(out, dx, x, u, t, args...; kwargs...)
        out .= .... # update out
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
    New DAE system must be a subtype of `AbstractDAESystem` to function properly.


# Example

```julia
julia> @def_dae_system mutable struct MyDAESystem{RH, RO, ST, IP, OP} <: AbstractDAESystem
        righthandside::RH = function sfuncdae(out, dx, x, u, t)
                out[1] = x[1] + 1 - dx[1]
                out[2] = (x[1] + 1) * x[2] + 2
            end 
        readout::RO = (x,u,t) -> x 
        state::ST = [1., -1]
        stateder::ST = [2., 0]
        diffvars::Vector{Bool} = [true, false]
        input::IP = nothing 
        output::OP = Outport(1)
        end

julia> ds = MyDAESystem();
```
