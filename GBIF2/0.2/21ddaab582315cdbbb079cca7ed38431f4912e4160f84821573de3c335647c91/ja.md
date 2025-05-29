```
species(key; kw...)
species(key, resulttype; kw...)
```

GBIF `species` APIをクエリし、単一の`Species`を返します。

  * `key`: 種のキー、またはキーを取得できる別の検索からの`Species`オブジェクト。
  * `resulttype`: これを設定すると、`Species`の代わりに、`species`は`(:verbatim, :name, :parents, :children, :related, :synonyms, :combinations, :descriptions, :distributions, :media, :references, :speciesProfiles, :vernacularNames, :typeSpecimens)`のいずれかのオブジェクトを返します。返される値は生の`JSON3.Object`ですが、その`propertynames`を確認してデータにアクセスするために使用できます。

# 例

ここでは、`species_search`を使用して種を見つけ、その後`species`で完全なレコードを取得します。

```julia
julia> using GBIF2
julia> tbl = species_search("Falco punctatus")
20-element GBIF2.Table{GBIF2.Species, JSON3.Array{JSON3.Object, Vector{UInt8}, SubArray{
UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}
┌──────────┬──────────┬───────────────┬───────────────┬────────────┬─────────┬──────────
│  kingdom │   phylum │         class │         order │     family │   genus │         ⋯
│  String? │  String? │       String? │       String? │    String? │ String? │         ⋯
├──────────┼──────────┼───────────────┼───────────────┼────────────┼─────────┼──────────
│ Animalia │  missing │          Aves │ Falconiformes │ Falconidae │ missing │ Falco p ⋯
│ Animalia │  missing │          Aves │       missing │ Falconidae │   Falco │ Falco p ⋯
│  missing │  missing │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│  missing │ Chordata │       missing │       missing │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│  Metazoa │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │  missing │       missing │ Falconiformes │ Falconidae │ missing │ Falco p ⋯
│  Metazoa │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│    ⋮     │    ⋮     │       ⋮       │       ⋮       │     ⋮      │    ⋮    │         ⋱
└──────────┴──────────┴───────────────┴───────────────┴────────────┴─────────┴──────────
                                                           35 columns and 11 rows omitted

```

そして、マッチの1つのすべてのフィールドを取得します。

```julia
julia> species(tbl[6])
GBIF2.Species({
                   "key": 102091853,
                "nubKey": 2481005,
               "nameKey": 4400647,
               "taxonID": "175650",
               "kingdom": "Animalia",
                "phylum": "Chordata",
                 "order": "Falconiformes",
                "family": "Falconidae",
                 "genus": "Falco",
               "species": "Falco punctatus",
            "kingdomKey": 101683523,
             "phylumKey": 102017110,
              "classKey": 102085317,
              "orderKey": 102091762,
             "familyKey": 102091763,
              "genusKey": 102091765,
            "speciesKey": 102091853,
            "datasetKey": "9ca92552-f23a-41a8-a140-01abaa31c931",
             "parentKey": 102091765,
                "parent": "Falco",
        "scientificName": "Falco punctatus Temminck, 1821",
         "canonicalName": "Falco punctatus",
        "vernacularName": "モーリシャス・ケストレル",
            "authorship": "Temminck, 1821",
              "nameType": "SCIENTIFIC",
                  "rank": "SPECIES",
                "origin": "SOURCE",
       "taxonomicStatus": "ACCEPTED",
   "nomenclaturalStatus": [],
        "numDescendants": 0,
           "lastCrawled": "2022-10-10T18:15:33.989+00:00",
       "lastInterpreted": "2022-10-10T19:16:16.841+00:00",
                "issues": [
                            "SCIENTIFIC_NAME_ASSEMBLED"
                          ],
               "synonym": false,
                 "class": "Aves"
})
```

## キーワード引数

  * `language`: 単一の引数または`(:parents, :children, :related, :synonyms)`の2番目の引数として指定できます。
  * `datasetKey`: 指定でき、2番目の引数`：related`とともに使用できます。

```
