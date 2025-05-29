```
stabilizeextractor(e::Extractor)
```

`e`と同様の構造を持ち、葉に`StableExtractor`を含む新しいエクストラクタを返します。

# 例

```jldoctest
julia> e = (a=ScalarExtractor(), b=CategoricalExtractor(1:5)) |> DictExtractor
DictExtractor
  ├── a: ScalarExtractor(c=0.0, s=1.0)
  ╰── b: CategoricalExtractor(n=6)

julia> e_stable = stabilizeextractor(e)
DictExtractor
  ├── a: StableExtractor(ScalarExtractor(c=0.0, s=1.0))
  ╰── b: StableExtractor(CategoricalExtractor(n=6))

julia> e(Dict("a" => 0))
ERROR: IncompatibleExtractor at path [:b]: this path contains missing data not supported by this extractor! See the `Stable Extractors` section in the docs.
[...]

julia> e_stable(Dict("a" => 0))
ProductNode  1 obs
  ├── a: ArrayNode(1×1 Array with Union{Missing, Float32} elements)  1 obs
  ╰── b: ArrayNode(6×1 MaybeHotMatrix with Union{Missing, Bool} elements)  1 obs
```

参照: [`suggestextractor`](@ref), [`extract`](@ref).
