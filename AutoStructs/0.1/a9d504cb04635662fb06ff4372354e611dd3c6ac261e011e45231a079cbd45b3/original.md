```
@structdef function MyType(args...; kws...); ...; return MyType(f1, f2, ...); end
```

This is a macro for easily defining new types.

Typically the steps to define a new `struct` are:

1. Define a `struct MyType` with the desired fields.
2. Define a constructor function like `MyType(arg1, arg2, ...)`, which initialises the fields.

This macro combines these steps into one, by taking the constructor definition of step 2 and using the return line to automatically infer the field names  and define the `struct`.

Moreover, if you change the name or types of the fields,  then the `struct` definition is automatically replaced. This works because this definition uses an auto-generated name, and `MyType` becomes an alias to it. Thanks to this, you can easily experiment with different field names and types,  overcoming a major limitation of a Revise.jl workflow.

Subtyping is also supported, by adding a `<: Supertype` to the return line.

## Examples

```julia
@structdef function Layer(din::Int, dout::Int)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight, bias)
end

layer = Layer(2, 4)
layer isa Layer  # true
```

The `@structdef` definition above is equivalent to the following code:

```julia
@kwdef struct Layer001{T1, T2}
    weight::T1
    bias::T2
end

function Layer001(din::Int, dout::Int)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer001(weight, bias)
end

Layer = Layer001

Base.show(io::IO, x::Layer) = ... # we do some pretty printing
Base.show(io::IO, ::MIME"text/plain", x::Layer) = ... 
```

Since `Layer001{T1, T2}` can hold any objects, even `Layer("hello", "world")`,  there should never be an ambiguity between the `struct`'s own constructor,  and your constructor function. If the two have the same number of arguments, you can avoid the ambiguity by using type restrictions in the input arguments (as in the example above) or in the return line:

```julia
@structdef function Layer(din, dout)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight::AbstractMatrix, bias::AbstractVector)
end

layer = Layer(2, 4)
```

This creates a struct like this:

```julia
@kwdef struct Layer002{T1<:AbstractMatrix, T2<:AbstractVector}
    weight::T1
    bias::T2
end
```

and reassigns `Layer = Layer002`.

Finally, we can also define a struct that is a subtype of another type:

```julia
abstract type AbstractLayer end

@structdef function Layer(din, dout)
    weight = randn(dout, din)
    bias = zeros(dout)
    return Layer(weight, bias) <: AbstractLayer
end

layer = Layer(din=2, dout=4)
@assert layer isa AbstractLayer
```

The corresponding struct definition becomes

```julia
@kwdef struct Layer003{T1, T2} <: AbstractLayer
    weight::T1
    bias::T2
end
```
