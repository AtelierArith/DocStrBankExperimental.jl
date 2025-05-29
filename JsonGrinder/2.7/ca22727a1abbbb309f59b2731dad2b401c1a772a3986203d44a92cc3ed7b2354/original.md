```
DictExtractor{S} <: Extractor
```

Extracts all items in a `Dict` and returns them as a `Mill.ProductNode`.

# Examples

```jldoctest
julia> e = (a=ScalarExtractor(), b=CategoricalExtractor(1:5)) |> DictExtractor
DictExtractor
  ├── a: ScalarExtractor(c=0.0, s=1.0)
  ╰── b: CategoricalExtractor(n=6)

julia> e(Dict("a" => 1, "b" => 1))
ProductNode  1 obs
  ├── a: ArrayNode(1×1 Array with Float32 elements)  1 obs
  ╰── b: ArrayNode(6×1 OneHotArray with Bool elements)  1 obs
```
