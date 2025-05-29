```
has_plain_constructor(def, name = struct_name_plain(def))
```

Check if the struct definition contains the plain constructor of `name`. By default the name is the inferable name [`struct_name_plain`](@ref).

# Example

```julia
def = @expr JLKwStruct struct Foo{T, N}
    x::Int
    y::N

    Foo{T, N}(x, y) where {T, N} = new{T, N}(x, y)
end

has_plain_constructor(def) # true

def = @expr JLKwStruct struct Foo{T, N}
    x::T
    y::N

    Foo(x, y) = new{typeof(x), typeof(y)}(x, y)
end

has_plain_constructor(def) # false
```

the arguments must have no type annotations.

```julia
def = @expr JLKwStruct struct Foo{T, N}
    x::T
    y::N

    Foo{T, N}(x::T, y::N) where {T, N} = new{T, N}(x, y)
end

has_plain_constructor(def) # false
```
