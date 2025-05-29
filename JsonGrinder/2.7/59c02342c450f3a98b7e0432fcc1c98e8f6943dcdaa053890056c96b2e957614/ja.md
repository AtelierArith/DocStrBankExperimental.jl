```
extract(e::Extractor, samples; store_input=Val(false))
```

複数のサンプルを一度に効率的に抽出します。

`extract`が`samples`を**反復可能**なサンプルの（既知の長さの）集合として期待するのに対し、`e(sample)`を直接呼び出すことは**単一**のサンプルに対して機能します。言い換えれば、`e(sample)`は`extract(e, [sample])`と同等です。

関連情報: [`suggestextractor`](@ref), [`stabilizeextractor`](@ref), [`schema`](@ref)。

# 例

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
