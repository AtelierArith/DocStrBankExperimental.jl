```
HypertextLiteral
```

The `HypertextLiteral` module exports the `@htl` macro which implements interpolation aware of hypertext escape context. It also provides for escaping of JavaScript within the `<script>` tag.

```jldoctest
julia> v = "<1 Brown \"M&M's\"!";

julia> @htl "<span>$v</span>"
<span>&lt;1 Brown &quot;M&amp;M&apos;s&quot;!</span>

julia> @htl "<script>console.log($v)</script>"
<script>console.log("<1 Brown \"M&M's\"!")</script>
```

This escaping of Julia values to JavaScript values is done with `js` function, which is not exported by default.

```jldoctest
julia> v = "<1 Brown \"M&M's\"!";

julia> @htl "<div onclick='alert($(HypertextLiteral.js(v)))'>"
<div onclick='alert(&quot;&lt;1 Brown \&quot;M&amp;M&apos;s\&quot;!&quot;)'>
```

There is also a non-standard string literal, `@htl_str` that is not exported. It can be used with dynamically constructed templates.

See also: [`@htl`](@ref), [`HypertextLiteral.@htl_str`](@ref)
