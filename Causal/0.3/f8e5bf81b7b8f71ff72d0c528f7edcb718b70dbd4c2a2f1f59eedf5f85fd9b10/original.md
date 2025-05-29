```
@def_sink ex
```

where `ex` is the expression to define to define a new AbstractSink component type. The usage is as follows:

```julia
@def_sink struct MySink{T1,T2,T3,...,TN, A} <: AbstractSink
    param1::T1 = param1_default     # optional field 
    param2::T2 = param2_default     # optional field 
    param3::T3 = param3_default     # optional field
        ⋮
    paramN::TN = paramN_default     # optional field 
    action::A = action_function     # mandatory field
end
```

Here, `MySink` has `N` parameters and `action` function

!!! warning `action` function must have a method `action(sink::MySink, t, u)` where `t` is the time data and `u` is the data     flowing into the sink.

!!! warning New static system must be a subtype of `AbstractSink` to function properly.

# Example

```julia
julia> @def_sink struct MySink{A} <: AbstractSink 
       action::A = actionfunc
       end

julia> actionfunc(sink::MySink, t, u) = println(t, u)
actionfunc (generic function with 1 method)

julia> sink = MySink();

julia> sink.action(sink, ones(2), ones(2) * 2)
[1.0, 1.0][2.0, 2.0]
```
