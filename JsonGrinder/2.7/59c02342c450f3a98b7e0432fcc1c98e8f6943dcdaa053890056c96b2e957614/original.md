```
extract(e::Extractor, samples; store_input=Val(false))
```

Efficient extraction of multiple samples at once.

Note that whereas `extract` expects `samples` to be an **iterable** of samples (of known length), calling the extractor directly with `e(sample)` works for a **single** sample. In other words, `e(sample)` is equivalent to `extract(e, [sample])`.

See also: [`suggestextractor`](@ref), [`stabilizeextractor`](@ref), [`schema`](@ref).

# Examples

```jldoctest
julia> sample = Dict("a" => 0, "b" => "foo");

julia> e = suggestextractor(schema([sample]))
DictExtractor
  ├── a: CategoricalExtractor(n=2)
  ╰── b: CategoricalExtractor(n=2)

julia> e(sample)
ProductNode  1 obs
  ├── a: ArrayNode(2×1 OneHotArray with Bool elements)  1 obs
  ╰── b: ArrayNode(2×1 OneHotArray with Bool elements)  1 obs

julia> e(sample) == extract(e, [sample])
true
```
