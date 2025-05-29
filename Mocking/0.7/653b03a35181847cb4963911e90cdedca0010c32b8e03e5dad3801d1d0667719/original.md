```
apply(body::Function, patches; debug::Bool=false) -> Any
```

Applies one or more `patches` during execution of `body`. Specifically ,any [`@mock`](@ref) call sites encountered while running `body` will include the provided `patches` when performing dispatch.

Multiple-dispatch is used to determine which method to call when utilizing multiple patches. However, patch defined methods always take precedence over the original function methods.

!!! note
    Ensure you have called [`activate`](@ref) prior to calling `apply` as otherwise the provided patches will be ignored.


See also: [`@mock`](@ref), [`@patch`](@ref).

## Examples

Applying a patch allows the alternative patch function to be called:

```jldoctest
julia> f() = "original";

julia> p = @patch f() = "patched";

julia> apply(p) do
            @mock f()
       end
"patched"
```

Patches take precedence over the original function even when the original method is more specific:

```jldoctest
julia> f(::Int) = "original";

julia> p = @patch f(::Any) = "patched";

julia> apply(p) do
            @mock f(1)
       end
"patched"
```

However, when the patches do not provide a valid method to call then the original function will be used as a fallback:

```jldoctest
julia> f(::Int) = "original";

julia> p = @patch f(::Char) = "patched";

julia> apply(p) do
           @mock f(1)
       end
"original"
```

### Nesting

Nesting multiple [`apply`](@ref) calls is allowed. When multiple patches are provided for the same method then the innermost patch takes precedence:

```jldoctest
julia> f() = "original";

julia> p1 = @patch f() = "p1";

julia> p2 = @patch f() = "p2";

julia> apply(p1) do
           apply(p2) do
               @mock f()
           end
       end
"p2"
```

When multiple patches are provided for different methods then multiple-dispatch is used to select the most specific patch:

```jldoctest
julia> f(::Int) = "original";

julia> p1 = @patch f(::Integer) = "p1";

julia> p2 = @patch f(::Number) = "p2";

julia> apply(p1) do
           apply(p2) do
               @mock f(1)
           end
       end
"p1"
```
