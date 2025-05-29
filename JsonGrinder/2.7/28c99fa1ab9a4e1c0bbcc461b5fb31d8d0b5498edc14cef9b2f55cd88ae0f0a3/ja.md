```
suggestextractor(e::Schema; min_occurences=1, all_stable=false, categorical_limit=100)
```

与えられたスキーマ `e` に基づいて、対応する `Extractor` を作成します。

  * `min_occurences` は、エクストラクタに含めるためのキーの最小出現回数を指定します。
  * `all_stable` は、すべてのリーフエクストラクタを厳密に安定にします。
  * `categorical_limit` は、リーフがカテゴリ変数と見なされるための異なる値の最大数を指定します。
  * `ngram_params` は、`NGramExtractor` のデフォルトパラメータをオーバーライドすることを可能にします。

# 例

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

参照: [`extract`](@ref), [`stabilizeextractor`](@ref).
