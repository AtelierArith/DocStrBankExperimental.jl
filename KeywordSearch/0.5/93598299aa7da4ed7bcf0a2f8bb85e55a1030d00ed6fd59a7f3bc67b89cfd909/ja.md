```
NamedQuery(metadata::Union{String, NamedTuple}, query::AbstractQuery)
```

クエリに関する情報を保持するメタデータフィールドを格納する `NamedQuery` を作成します。 `match` と共に使用すると、`NamedQuery` のメタデータと一致したオブジェクトのメタデータを持つ [`NamedMatch`](@ref) を返します。

## 例

```jldoctest
julia> document_1 = Document("One", (; document_name = "a"))
Document with text "One ". Metadata: (document_name = "a",)

julia> document_2 = Document("Two", (; document_name = "b"))
Document with text "Two ". Metadata: (document_name = "b",)

julia> corpus = Corpus([document_1, document_2], (; corpus_name = "Numbers"))
Corpus with 2 documents, each with metadata keys: (:document_name,)
Corpus metadata: (corpus_name = "Numbers",)

julia> query = NamedQuery(FuzzyQuery("one"), "find one")
NamedQuery
├─ (query_name = "find one",)
└─ FuzzyQuery("one", DamerauLevenshtein{Nothing}(nothing), 2)

julia> m = match(query, corpus)
NamedMatch
├─ (query_name = "find one", corpus_name = "Numbers", document_name = "a")
└─ QueryMatch with distance 1 at indices 1:3.
   ├─ FuzzyQuery("one", DamerauLevenshtein{Nothing}(nothing), 2)
   └─ Document with text "One ". Metadata: (document_name = "a",)

julia> m.metadata
(query_name = "find one", corpus_name = "Numbers", document_name = "a")
```
