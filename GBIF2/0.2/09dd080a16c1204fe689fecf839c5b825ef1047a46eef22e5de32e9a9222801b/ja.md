```
species_match(; kw...)
```

GBIFの`species/match` APIをクエリし、ファジー検索を使用して最も近い単一の`Species`を返します。

結果は特に詳細ではなく、`species_match`の結果に対して`species(res)`を呼び出すことで、完全なデータセットをクエリすることで改善できます。

# 例

```julia
using GBIF2
sp = species_match("Lalage newtoni")

# 出力
GBIF2.Species({
           "usageKey": 8385394,
   "acceptedUsageKey": 2486791,
     "scientificName": "Lalage newtoni (Pollen, 1866)",
      "canonicalName": "Lalage newtoni",
               "rank": "SPECIES",
             "status": "SYNONYM",
         "confidence": 98,
          "matchType": "EXACT",
            "kingdom": "Animalia",
             "phylum": "Chordata",
              "order": "Passeriformes",
             "family": "Campephagidae",
              "genus": "Coracina",
            "species": "Coracina newtoni",
         "kingdomKey": 1,
          "phylumKey": 44,
           "classKey": 212,
           "orderKey": 729,
          "familyKey": 9284,
           "genusKey": 2482359,
         "speciesKey": 2486791,
            "synonym": true,
              "class": "Aves"
})
```

## キーワード

キーワードは[GBIF API](https://www.gbif.org/developer/species)に正確に従って使用します。

キーワードの列挙値は`[GBIF2.enum](@ref)`関数で見つけることができます。

  * `rank`: 私たちのRank列挙型に示されている分類学的ランクでフィルタリングします
  * `name`: 種の名前
  * `strict`: `true`の場合、指定された名前のみを（ファジーに）一致させますが、上位分類のタクソンには決して一致しません
  * `verbose`: `true`の場合、考慮されたが拒否された代替の一致を表示します
  * `kingdom`: 標準名を受け入れるオプションの王国分類。
  * `phylum`: 標準名を受け入れるオプションの門分類。
  * `class`: 標準名を受け入れるオプションのクラス分類。
  * `order`: 標準名を受け入れるオプションの目分類。
  * `family`: 標準名を受け入れるオプションの科分類。
  * `genus`: 標準名を受け入れるオプションの属分類。
