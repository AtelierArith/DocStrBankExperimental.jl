```
@def_static_system ex
```

where `ex` is the expression to define to define a new AbstractStaticSystem component type. The usage is as follows:

```julia
@def_source struct MyStaticSystem{T1,T2,T3,...,TN,OP, RO} <: AbstractStaticSystem
    param1::T1 = param1_default     # optional field 
    param2::T2 = param2_default     # optional field 
    param3::T3 = param3_default     # optional field
        ⋮
    paramN::TN = paramN_default     # optional field 
    input::IP = input_default       # mandatory field
    output::OP = output_default     # mandatory field 
    readout::RO = readout_function  # mandatory field
end
```

Here, `MyStaticSystem` has `N` parameters, an `output` port, an `input` port and a `readout` function.

!!! warning
    `input`, `output` and `readout` are mandatory fields to define a new static system. The rest of the fields are the parameters of the system.


!!! warning
    `readout` must be a two-argument function, i.e. a function of time `t` and input value `u`.


!!! warning
    New static system must be a subtype of `AbstractStaticSystem` to function properly.


# Example

```julia
julia> @def_static_system struct MyStaticSystem{IP, OP, RO} <: AbstractStaticSystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       input::IP = Inport() 
       output::OP = Outport() 
       readout::RO = (t,u) -> α * u[1] + β * u[2]
       end

julia> sys = MyStaticSystem(); 

julia> sys.α
1.0

julia> sys.input
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
