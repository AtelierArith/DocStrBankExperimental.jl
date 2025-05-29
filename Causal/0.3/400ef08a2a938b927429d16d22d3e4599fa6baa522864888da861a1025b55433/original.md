```
@def_source ex
```

where `ex` is the expression to define to define a new AbstractSource component type. The usage is as follows:

```julia
@def_source struct MySource{T1,T2,T3,...,TN,OP, RO} <: AbstractSource
    param1::T1 = param1_default     # optional field 
    param2::T2 = param2_default     # optional field 
    param3::T3 = param3_default     # optional field
        ⋮
    paramN::TN = paramN_default     # optional field 
    output::OP = output_default     # mandatory field 
    readout::RO = readout_function  # mandatory field
end
```

Here, `MySource` has `N` parameters, an `output` port and a `readout` function.

!!! warning
    `output` and `readout` are mandatory fields to define a new source. The rest of the fields are the parameters of the source.


!!! warning
    `readout` must be a single-argument function, i.e. a function of time `t`.


!!! warning
    New source must be a subtype of `AbstractSource` to function properly.


# Example

```julia
julia> @def_source struct MySource{OP, RO} <: AbstractSource
       a::Int = 1 
       b::Float64 = 2. 
       output::OP = Outport() 
       readout::RO = t -> (a + b) * sin(t)
       end

julia> gen = MySource();

julia> gen.a 
1

julia> gen.output
1-element Outport{Outpin{Float64}}:
 Outpin(eltype:Float64, isbound:false)
```
