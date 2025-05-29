```
deep_properties(::Type{<:MLJType})
```

Given an `MLJType` subtype `M`, the value of this trait should be a tuple of any properties of `M` to be regarded as "deep".

When two instances of type `M` are to be tested for equality, in the sense of `==` or `is_same_except`, then the values of a "deep" property (whose values are assumed to be of composite type) are deemed to agree if all corresponding properties *of those property values* are `==`.

Any property of `M` whose values are themselves of `MLJType` are "deep" automatically, and should not be included in the trait return value.

See also [`is_same_except`](@ref)

### Example

Consider an `MLJType` subtype `Foo`, with a single field of type `Bar` which is *not* a subtype of `MLJType`:

```julia
mutable struct Bar
    x::Int
end

mutable struct Foo <: MLJType
    bar::Bar
end
```

Then the mutability of `Foo` implies `Foo(1) != Foo(1)` and so, by the definition `==` for `MLJType` objects (see [`is_same_except`](@ref)) we have

```julia
Bar(Foo(1)) != Bar(Foo(1))
```

However after the declaration

```julia
MLJModelInterface.deep_properties(::Type{<:Foo}) = (:bar,)
```

We have

```julia
Bar(Foo(1)) == Bar(Foo(1))
```
