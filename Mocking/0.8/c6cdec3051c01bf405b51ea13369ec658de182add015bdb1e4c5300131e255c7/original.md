```
@mock expr
```

Allows the call site function to be temporarily overloaded via an applied patch.

The `@mock` macro works as no-op until `Mocking.activate` has been called. Once Mocking has been activated then alternative methods defined via [`@patch`](@ref) can be used with [`apply`](@ref) to call the patched methods from within the `apply` context.

See also: [`@patch`](@ref), [`apply`](@ref).

## Examples

```jldoctest; setup=:(using Dates: Dates)
julia> f() = @mock time();

julia> p = @patch time() = 0.0;  # UNIX epoch

julia> apply(p) do
           Dates.unix2datetime(f())
       end
1970-01-01T00:00:00
```
