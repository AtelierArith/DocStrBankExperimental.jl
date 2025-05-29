```
species_search([q]; kw...)
```

GBIF `species/search` APIをクエリし、[`GBIF2.Table`](@ref)で多くの結果を返します。

# 例

```julia
using GBIF2
sp = species_search("Psittacula eques")

# 出力
20-element GBIF2.Table{GBIF2.Species, JSON3.Array{JSON3.Object, Vector{UInt8}, SubArray{UInt64, 1,
Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}
┌──────────┬──────────┬────────────────┬────────────────┬───────────────┬──────────────┬──
│  kingdom │   phylum │          class │          order │        family │        genus │ ⋯
│  String? │  String? │        String? │        String? │       String? │      String? │ ⋯
├──────────┼──────────┼────────────────┼────────────────┼───────────────┼──────────────┼──
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│ Animalia │  missing │        missing │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│  missing │  missing │        missing │        missing │       missing │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │        missing │   Psittacidae │   Psittacula │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ ANIMALIA │ CHORDATA │ PSITTACIFORMES │           AVES │   PSITTACIDAE │ Alexandrinus │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│    ⋮     │    ⋮     │       ⋮        │       ⋮        │       ⋮       │      ⋮       │ ⋱
└──────────┴──────────┴────────────────┴────────────────┴───────────────┴──────────────┴──
                                                              37 columns and 4 rows omitted
```

## キーワード引数

キーワードは[GBIF API](https://www.gbif.org/developer/species)と同じように使用します。

  * `class`: 標準名を受け入れるオプションのクラス分類。
  * `datasetKey`: チェックリストデータセットキー（UUID）でフィルタリングします。
  * `facet`: フィールドの最も頻繁な100の値を取得するために使用されるファセット名のリスト。許可されるファセットは`:datasetKey`、`:higherTaxonKey`、`:rank`、`:status`、`:nomenclaturalStatus`、`isExtinct`、`:habitat`、`:threat`および`:nameType`です。
  * `facetMincount`: ファセットパラメータと組み合わせて使用されます。`facetMincount=N`を設定すると、カウントがN未満のファセットを除外します。例えば、`facet=type, limit=>0, facetMincount=>10000`は、`OCCURRENCE`というタイプ値のみを表示します。なぜなら、`:CHECKLIST`と`:METADATA`は10000未満のカウントを持っているからです。
  * `facetMultiselect`: ファセットパラメータと組み合わせて使用されます。`facetMultiselect=true`を設定すると、現在フィルタリングされていない値のカウントも返されます。例えば、`facet=type, limit=>0, type=>CHECKLIST, facetMultiselect=>true`は、`type`が`type=:CHECKLIST`でフィルタリングされているにもかかわらず、`OCCURRENCE`と`METADATA`のタイプ値を表示します。
  * `family`: 標準名を受け入れるオプションの科分類。
  * `genus`: 標準名を受け入れるオプションの属分類。
  * `habitat`: 生息地でフィルタリングします。現在、私たちのHabitat enumでは3つの主要なバイオームのみが受け入れられています。
  * `highertaxonKey`: いずれかの上位リンネ階級キーでフィルタリングします。これはそれぞれのチェックリスト内であり、すべてのチェックリストを通じてnubキーを検索するわけではありません。
  * `hl`: フルテキスト検索フィールドでクエリに一致する用語を強調表示するには、`hl=true`を設定します。強調表示はクラス'gbifH1'の強調タグになります。例えば、`q="plant", hl=>true`。フルテキスト検索フィールドには、タイトル、キーワード、国、出版国、出版組織のタイトル、ホスティング組織のタイトル、および説明が含まれます。メタデータ文書からの情報を含む追加のフルテキストフィールドも検索されますが、このフィールドのテキストは応答には返されません。
  * `isExtinct`: 絶滅状態でフィルタリングします（ブール値、例：isExtinct=>true）。
  * `issue`: 私たちのNameUsageIssue enumで定義された特定のインデックスの問題。
  * `kingdom`: 標準名を受け入れるオプションの王国分類。
  * `language`: 私たちのISO 639-1の2文字コードとして与えられた、俗名の言語。
  * `nameType`: 私たちのNameType enumで与えられた名前のタイプでフィルタリングします。
  * `nomenclaturalStatus`: まだ実装されていませんが、最終的には命名法的地位enumでフィルタリングできるようになります。
  * `order`: 標準名を受け入れるオプションの目分類。
  * `phylum`: 標準名を受け入れるオプションの門分類。
  * `q`: シンプルなフルテキスト検索パラメータ。このパラメータの値は、単語またはフレーズのいずれかです。ワイルドカードはサポートされていません。
  * `rank`: 私たちのRank enumで与えられた分類学的ランクでフィルタリングします。
  * `sourceId`: ソース識別子でフィルタリングします。
  * `status`: 私たちのTaxonomicStatus enumで与えられた分類学的ステータスでフィルタリングします。
  * `strict`: `true`の場合、与えられた名前のみを（あいまいに）一致させますが、上位分類のタクソンには一致しません。
  * `threat`: 私たちのThreatStatus enumで与えられた分類学的脅威ステータスでフィルタリングします。
  * `verbose`: `true`の場合、考慮されたが拒否された代替の一致を表示します。
  * `offset`: 結果を開始するオフセット。
  * `limit`: 返す最大結果数。この値は300を超えることはできず、それを超える値は300に設定されます。

```
