```
@pack [context] target [in format] [(constructor...)] [{type parameters...}] [[formats...]]
```

Convenience macro to generate packing / unpacking code for the types specified by `target`.

## Arguments

### target

This argument has to be of the form `T`, `{<: T}`, or `{S <: T}`, where `T` is an existing type and `S` is a variable name that can be reused in the constructor (see below). This is the only mandatory argument of [`@pack`](@ref).

### context

This (optional) argument has to be an existing subtype `C <: Context`, see [`Context`](@ref). The generated code will be restricted to this context. Note that no instance of `C` can be passed; an actual type is required.

### format

This (optional) pattern can be used to set the default format of the type target by specializing the function [`format`](@ref). For instance, `@pack T in F` for `F <: Format` will define `StructPack.format(::Type{T}) = F()`.

The special syntax `F[C]`, where `F <: Format` and `C <: Context`, is available as shortcut for `ContextFormat{C, F}`. This will mainly be useful for the specification of field and type-parameter formats via `(formats...)`, see below.

### constructor

This (optional) argument affects the functions [`destruct`](@ref), [`construct`](@ref), [`fieldnames`](@ref), and (optionally) [`fieldtypes`](@ref) when a value of type `T` is packed / unpacked in a format `F <: AbstractStructFormat`.

  * It can be a list of (keyword) arguments like `(a, b, ...; c, d, ...)`, in which case the constructor `T` is called with the respective arguments in [`construct`](@ref).
  * It can be function call expression like `f(a, b, ...; c, d, ...)`, in which case the function `f` is called with the respective arguments in [`construct`](@ref).

In both cases, only the fields `(:a, :b, ..., :c, :d, ...)` are returned by [`fieldnames`](@ref), in this order. This also affects which fields are packed via [`destruct`](@ref).

If type specifications are present (e.g., `(a::Int, b; c::Float64)`), the respective field types returned by [`fieldtypes`](@ref) are overwritten.

### type parameters

This (optional) argument affects the function [`typeparamtypes`](@ref). It expects an expression of the form `{A::Ta, B::Tb, ...}`, where the labels `A, B, ...` are optional and `Ta, Tb, ...` indicate the type of the respective type parameter.

Specification of the type parameter types is necessary if `T` is to be packed / unpacked in [`TypeFormat`](@ref) or a value `val::T` is to be packed / unpacked in [`TypedFormat`](@ref).

As a simple example, consider `@pack {<: Array} {::Type, ::Int}`, which enables packing / unpacking of base array types:

```
@pack {<: Array} {::Type, ::Int}
bytes = pack(Array{Float64, 3})
unpack(bytes, Type) # sucessfully returns Array{Float64, 3}
```

### formats

This (optional) argument affects the functions [`fieldformats`](@ref) and [`typeparamformats`](@ref). It is expected to be a list of format specifications `[a in Fa, b in Fb, C in FC, ...]`, where the labels `a, b, C, ...` refer to either field names of `T` or type parameter names established in the `{type parameters...}` argument, and where `Fa, Fb, FC, ...` are existing subtypes of `Format` (see `in format` above).

For convenience, the syntax `[(a, b, ...) in F]` translates to `[a in F, b in F, ...]`.

## Examples

```julia
using StructPack

struct A
  a :: Int
  b :: Vector{Float64}
  c :: Vector{Float64}
end

A(a, b) = A(a, b, rand(5))

@pack A in StructFormat (a, b) [b in BinVectorFormat]

A(a, b; c) = A(a, b, c)

@pack A in StructFormat (a, b; c) [(b, c) in BinVectorFormat]

myA(a) = A(a, [], [])

@pack A in StructFormat myA(a)
```
