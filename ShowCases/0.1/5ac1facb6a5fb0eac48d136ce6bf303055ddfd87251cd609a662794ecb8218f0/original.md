```
ShowLimit
```

An `AbstractShow` wrapper for showing an object with the shown string limited to a fixed number of characters.

## Constructors

  * `ShowLimit(o; limit=typemax(Int), n=0, continuation_string="…", check_brackets=true)`

## Arguments

  * `o`: the object to be wrapped.
  * `limit`: the maximum number of characters, excluding starting delimiters and the continuation string, which can be shown.
  * `n::Integer`: the position of the start of the shown string.  This is useful if showing multiple outputs with a fixed limit.   For example, `n=1` with `limit=3` is equivalent to `limit=2`.
  * `continuation_string::AbstractString`: string to be printed if the limit is reached.  Not counted toward the limit.
  * `check_brackets`: whether to check for the existence of opening brackets at the beginning of the shown string. This is   useful for showing closing brackets regardless of whether the limit is reached.

## Examples

```
julia> ShowLimit(123, limit=2)
12…

julia> ShowLimit("abc", limit=2)
"a…"

julia> ShowLimit("abc", limit=2, check_brackets=false)
"a…

julia> ShowLimit(123, limit=2, n=1)
1…
```
