```
species_list(; kw...)
species_list(key; kw...)
species_list(key, resulttype; kw...)
```

GBIF `species_list` APIをクエリし、クエリに正確に一致する`Species`のテーブルを返します。

# 例

```julia
using GBIF2
species_list(; name="Lalage newtoni")

# 出力
8-element GBIF2.Table{GBIF2.Species, JSON3.Array{JSON3.Object, Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}
┌──────────┬──────────┬───────────────┬───────────────┬───────────────┬──────────┬──────────────────┬───────────┬─────────┬──────────┬──────────────┬────────────────┬───────
│  kingdom │   phylum │         class │         order │        family │    genus │          species │       key │  nubKey │  nameKey │      taxonID │ sourceTaxonKey │ king ⋯
│  String? │  String? │       String? │       String? │       String? │  String? │          String? │    Int64? │  Int64? │   Int64? │      String? │         Int64? │      ⋯
├──────────┼──────────┼───────────────┼───────────────┼───────────────┼──────────┼──────────────────┼───────────┼─────────┼──────────┼──────────────┼────────────────┼───────
│ Animalia │ Chordata │          Aves │ Passeriformes │ Campephagidae │ Coracina │ Coracina newtoni │   8385394 │ missing │ 18882488 │ gbif:8385394 │      176651982 │      ⋯
│ Animalia │  missing │          Aves │       missing │ Campephagidae │   Lalage │   Lalage newtoni │ 100144670 │ 8385394 │  5976204 │        06014 │        missing │  128 ⋯
│ Animalia │  missing │          Aves │ Passeriformes │ Campephagidae │  missing │   Lalage newtoni │ 133165079 │ 8385394 │  5976204 │        18380 │        missing │  135 ⋯
│ Animalia │ Chordata │          Aves │ Passeriformes │ Campephagidae │   Lalage │   Lalage newtoni │ 161400685 │ 8385394 │ 18882488 │       895898 │        missing │  134 ⋯
│  missing │  missing │       missing │       missing │       missing │ Bossiaea │   Lalage newtoni │ 165585935 │ missing │ 18882488 │      6924877 │        missing │    m ⋯
│ Animalia │  missing │          Aves │ Passeriformes │ Campephagidae │   Lalage │   Lalage newtoni │ 165923305 │ 8385394 │ 18882488 │        19393 │        missing │  100 ⋯
│ Animalia │ Chordata │          Aves │ Passeriformes │ Campephagidae │   Lalage │   Lalage newtoni │ 168010293 │ 8385394 │  5976204 │       181376 │        missing │  167 ⋯
│ Animalia │ Chordata │ Passeriformes │          Aves │ Campephagidae │   Lalage │   Lalage newtoni │ 176651982 │ 8385394 │ 18882488 │     22706569 │        missing │  202 ⋯
└──────────┴──────────┴───────────────┴───────────────┴───────────────┴──────────┴──────────────────┴───────────┴─────────┴──────────┴──────────────┴────────────────┴───────
```

## キーワード引数

私たちは、[GBIF API](https://www.gbif.org/developer/species)とまったく同じようにキーワードを使用します。

キーワードの列挙値は、`[GBIF2.enum](@ref)`関数で見つけることができます。

  * `language`: 俗称の言語、ISO 639-1の2文字コードとして指定
  * `datasetKey`: チェックリストデータセットキー（UUID）でフィルタリング
  * `sourceId`: ソース識別子でフィルタリング
  * `name`: 種の名前
  * `offset`: 結果の開始オフセット
  * `limit`: 返す結果の最大数。この値は300を超えることはできず、それを超える値は300に設定されます。
