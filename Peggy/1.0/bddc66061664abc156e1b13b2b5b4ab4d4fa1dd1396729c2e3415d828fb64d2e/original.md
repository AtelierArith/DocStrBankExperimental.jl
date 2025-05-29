```
CHAR(charclass::String)
```

Create a parser for a single character matchng regex character classes. 

Functionally identical to Regex("[:charclass]") except it is known to never match an empty string.  This is important to avoid unneccesary and expensive left-recursion overhead.

# Examples

```jldoctet
julia> g = @grammar begin
       number = [ digit ds:(digit...)  { parse(Int, *(digit, ds...)) } ]
       digit = CHAR("[:digit:]")
       end;

julia> g("1234")
1234
```
