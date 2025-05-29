```
suggestextractor(e::Schema; min_occurences=1, all_stable=false, categorical_limit=100)
```

given schema `e`, create a corresponding `Extractor`

  * `min_occurences` specifies the minimum occurence of a key to be included in the extractor.
  * `all_stable` makes all leaf extractors strictly stable.
  * `categorical_limit` specifies the maximum number of different values in a leaf for it to be   considered a categorical variable.
  * `ngram_params` makes it possible to override default params for `NGramExtractor`.

# Examples

```jldoctest
julia> s = schema([ Dict("a" => 1, "b" => ["foo"], "c" => Dict("d" => 1)),
                    Dict("a" => 2,                 "c" => Dict())])
DictEntry 2x updated
  ├── a: LeafEntry (2 unique `Real` values) 2x updated
  ├── b: ArrayEntry 1x updated
  │        ╰── LeafEntry (1 unique `String` values) 1x updated
  ╰── c: DictEntry 2x updated
           ╰── d: LeafEntry (1 unique `Real` values) 1x updated

julia> suggestextractor(s)
DictExtractor
  ├── a: CategoricalExtractor(n=3)
  ├── b: ArrayExtractor
  │        ╰── StableExtractor(CategoricalExtractor(n=2))
  ╰── c: DictExtractor
           ╰── d: StableExtractor(CategoricalExtractor(n=2))

julia> suggestextractor(s; all_stable=true)
DictExtractor
  ├── a: StableExtractor(CategoricalExtractor(n=3))
  ├── b: ArrayExtractor
  │        ╰── StableExtractor(CategoricalExtractor(n=2))
  ╰── c: DictExtractor
           ╰── d: StableExtractor(CategoricalExtractor(n=2))

julia> suggestextractor(s; min_occurences=2)
DictExtractor
  ╰── a: CategoricalExtractor(n=3)

julia> suggestextractor(s; categorical_limit=0)
DictExtractor
  ├── a: ScalarExtractor(c=1.0, s=1.0)
  ├── b: ArrayExtractor
  │        ╰── StableExtractor(NGramExtractor(n=3, b=256, m=2053))
  ╰── c: DictExtractor
           ╰── d: StableExtractor(ScalarExtractor(c=1.0, s=1.0))
```

See also: [`extract`](@ref), [`stabilizeextractor`](@ref).
