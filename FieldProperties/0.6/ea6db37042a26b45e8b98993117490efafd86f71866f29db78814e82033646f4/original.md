```
@defprop Property{name}::Type block
```

Convient way of creating properties that wrap `getproperty` and `setproperty!` methods.

## Examples

The simplest form simply creates a getter and setter.

```jldoctest defprop
julia> using FieldProperties

julia> @defprop Property1{:prop1}

julia> name(prop1)
:prop1

julia> prop1_type(:any_type)
Any
```

Define the propertie's type

```jldoctest defprop
julia> @defprop Property2{:prop2}::Int

julia> name(prop2)
:prop2

julia> prop2_type(:any_type)
Int64
```

Define type requirement and default value.

```jldoctest defprop
julia> @defprop Property3{:prop3}::Int begin
           @getproperty x -> 1
       end

julia> name(prop3)
:prop3

julia> prop3_type(:any_type)
Int64

julia> prop3(3)
1
```

Define a default value but no enforced return type but multiple `getproperty` methods.

```jldoctest defprop
julia> @defprop Property4{:prop4} begin
           @getproperty x::Int -> 1
           @getproperty x::String -> "1"
       end

julia> name(prop4)
:prop4

julia> prop4_type(:any_type)
Any

julia> prop4(1)
1
```
