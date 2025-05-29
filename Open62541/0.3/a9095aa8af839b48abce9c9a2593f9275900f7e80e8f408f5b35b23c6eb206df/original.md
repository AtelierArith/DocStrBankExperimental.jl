```
JUA_Argument
```

A mutable struct that defines a `JUA_Argument` object - the equivalent of a `UA_Argument`, but with memory managed by Julia rather than C (exceptions below).

The following constructor methods are defined:

```
JUA_Argument()
```

creates an empty `JUA_Argument`, equivalent to calling `UA_Argument_new()`.

```
JUA_Argument(examplearg::Union{Nothing, AbstractArray{<: ARG_TYPEUNION}, ARG_TYPEUNION} = nothing; 
        name::Union{Nothing, AbstractString} = nothing, 
        description::Union{AbstractString, Nothing} = nothing, 
        localization::AbstractString = "en-US",
        datatype::Union{Nothing, ARG_TYPEUNION} = nothing,
        valuerank::Union{Integer, Nothing} = nothing, 
        arraydimensions::Union{Integer, AbstractArray{<: Integer}, Nothing} = nothing)
```

creates a `JUA_Argument` based on the properties of `examplearg`. Specifically, the `datatype`, `valuerank`, and `arraydimensions` are automatically determined from `examplearg`. The `name`, `description` and `localization` keyword arguments can be used to describe the `JUA_Argument` further.

The `valuerank` and `arraydimensions` properties are explained here: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.6)

```
JUA_Argument(argumentptr::Ptr{UA_Argument})
```

creates a `JUA_Argument` based on the pointer `argumentptr`. This is a fallback method that can be used to pass `UA_Argument`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `argumentptr` needs to be manually cleaned up with `UA_Argument_delete(argumentptr)` after the object is not needed anymore. It is up to the user to ensure this.

Examples:

```
j = JUA_Argument()
j = JUA_Argument(1.0) #will accept a Float64 scalar
j = JUA_Argument(zeros(Float32, 2, 2)) #will exclusively accept Float32 arrays of size 2x2
j = JUA_Argument(zeros(Float32, 2, 2), arraydimensions = [0, 0]) #will accept any 2D Float32 array.
j = JUA_Argument(datatype = Int8, valuerank = 1, arraydimensions = [2, 2]) #will accept a Int8 array of size 2 x 2.
j = JUA_Argument(datatype = Float64, valuerank = 1, arraydimensions = 4) #will accept a Float64 vector with 4 elements.
j = JUA_Argument(datatype = Float64, valuerank = 1, arraydimensions = 0) #will accept a Float64 vector of any length.
```
