`StringArray{T,N}`

Efficient storage for N dimensional array of strings.

`StringArray` stores underlying string data for all elements of the array in a single contiguous buffer. It maintains offset and length for each element.

`T` can be `String`, `WeakRefString`, `EscapedString`, `Union{Missing, String}`, `Union{Missing, WeakRefString}`, or `Union{Missing, EscapedString}`. `getindex` will return this type except `EscapedString` returns the unescaped `String`.

You can use `convert(StringArray{U}, ::StringArray{T})` to change the element type (e.g. to `WeakRefString` for efficiency) without copying the data.

# Example construction

```
julia> sa = StringArray(["x", "y"]) # from Array{String}
2-element WeakRefStrings.StringArray{String,1}:
 "x"
 "y"

julia> sa = StringArray{WeakRefString}(["x", "y"])
2-element WeakRefStrings.StringArray{WeakRefStrings.WeakRefString,1}:
 "x"
 "y"

julia> sa = StringArray{Union{Missing, String}}(["x", "y"]) # with Missing
2-element WeakRefStrings.StringArray{Union{Missing, String},1}:
 "x"
 "y"

julia> sa = StringArray{Union{Missing, String}}(2,2) # undef
2×2 WeakRefStrings.StringArray{Union{Missing, String},2}:
 #undef  #undef
 #undef  #undef
```
