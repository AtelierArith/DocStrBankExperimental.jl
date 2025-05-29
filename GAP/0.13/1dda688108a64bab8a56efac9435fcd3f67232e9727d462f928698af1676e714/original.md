```
@g_str
```

Create a GAP string by typing `g"content"`.

# Examples

```jldoctest
julia> g"foo"
GAP: "foo"

julia> g"ab\ncd\"ef\\gh"   # special characters are handled as in GAP
GAP: "ab\ncd\"ef\\gh"

```

Due to Julia's way of handing over arguments into the code of macros, not all strings representing valid GAP strings can be processed.

```jldoctest
julia> g"\\"
ERROR: Error thrown by GAP: Syntax error: String must end with " before end of file in stream:1
[...]

```

Conversely, there are valid arguments for the macro that are not valid Julia strings.

```jldoctest
julia> g"\c"
GAP: "\c"

```
