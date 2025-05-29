```
macro >(body)
```

If body is in the form `object_ |> call_`, call [`@_`](@ref) on `call`, and recur on `object`.

```jldoctest chain
julia> using LightQuery


julia> @> 0 |> _ - 1 |> abs |> Base.abs
1
```

You can't include multiple arguments.

```jldoctest chain
julia> @> _ |> _ + __
ERROR: LoadError: ArgumentError: Chain segments must contain single underscores only
[...]
```

You can nest chains:

```jldoctest chain
julia> @> 1 |> (@> _ + 1 |> _ + 1)
3
```

Handles interpolations seamlessly:

```jldoctest chain
julia> @> 1 |> :(_ + $_)
:(_ + 1)
```
