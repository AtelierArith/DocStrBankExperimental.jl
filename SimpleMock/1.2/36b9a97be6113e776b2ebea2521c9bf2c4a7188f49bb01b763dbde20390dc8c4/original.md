```
mock(f::Function[, ctx::Symbol], args...; filters::Vector{<:Function}=Function[])
```

Run `f` with specified functions mocked out.

!!! note
    Mocking functions with keyword arguments is only partially supported. See the "Keyword Arguments" section below for more details.


## Examples

Mocking a single function:

```julia
f(x) = x + 1
mock(+) do plus
    @assert plus isa Mock
    @assert f(0) != 1  # The call to + is mocked.
    @assert called_once_with(plus, 0, 1)
end
```

Mocking a function with a custom [`Mock`](@ref):

```julia
mock((+) => Mock(1)) do plus
    @assert 1 + 1 == 1
    @assert called_once_with(plus, 1, 1)
end
```

Mocking methods that match a given signature:

```julia
mock((+, Float64, Float64) => Mock((a, b) -> 2a + 2b)) do plus
    @assert 1 + 1 == 2
    @assert 2.0 + 2.0 == 8
    @assert called_once_with(plus, 2.0, 2.0)
end
```

Mocking with something other than a `Mock`:

```julia
mock((+) => (a, b) -> 2a + 2b) do _plus
    @assert 1 + 2 == 6
end
```

## Using Filters

Oftentimes, you mock a function with a very specific idea of where you want that mocking to happen. It can be confusing when a call you didn't anticipate gets mocked somewhere deep in the call stack, botching everything. To avoid this, you can use filter functions like so:

```julia
f(x, y) = x + y
g(x, y) = f(x, y)
mock((+) => Mock((a, b) -> 2a + 2b); filters=[max_depth(2)]) do plus
    @assert f(1, 2) == 6  # The call depth of + here is 2.
    @assert g(3, 4) == 7  # Here, it's 3.
    @assert called_once_with(plus, 1, 2)
end
```

Filter functions take a single argument of type [`Metadata`](@ref). If any filter rejects, then mocking is not performed. See [Filter Functions](@ref) for a list of included filters, as well as building blocks for you to create your own.

## Reusing `Context`s

Under the hood, this function creates a new [Cassette `Context`](https://jrevels.github.io/Cassette.jl/stable/api.html#Cassette.Context) on every call by default. This provides a nice clean mocking environment, but it can be slow to create and call new types and methods over and over. If you find yourself repeatedly mocking the same set of functions, you can specify a context name to reuse that context like so:

```julia
ctx = gensym()
mock(g -> @assert(!called(g)), ctx, get)
# This one is faster, especially when there's a lot going on in your mock blocks.
mock(g -> @assert(!called(g)), ctx, get)
```

## Keyword Arguments

Mocking of functions with keyword arguments is fully supported when the following conditions are met:

  * Filter functions are not used
  * The context in use has no previously-mocked functions that are now unmocked

if a filter function rejects and calls a mocked function (instead of its mock), that call will have no keywords.

If you reuse a context that has previously mocked some function, unmocked calls to that function will have no keywords. For example:

```julia
kwfunc(; kwargs...) = nothing
calls_kwfunc(; kwargs...) = kwfunc(; kwargs...)
ctx = gensym()
mock(ctx, calls_kwfunc) do c
    calls_kwfunc(; x=1, y=2)
    @assert called_once_with(c; x=1, y=2)
end
mock(ctx, kwfunc) do k
    calls_kwfunc(; x=1, y=2)               # This will issue a warning.
    @assert called_once_with(k; x=1, y=2)  # This will fail!
end
```

In short, avoid using filters and reusing contexts when mocking functions that accept keywords.
