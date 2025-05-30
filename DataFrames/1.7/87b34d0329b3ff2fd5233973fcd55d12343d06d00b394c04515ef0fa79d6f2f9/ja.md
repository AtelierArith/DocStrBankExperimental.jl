```
leftjoin!(df1, df2; on, makeunique=false, source=nothing,
          matchmissing=:error)
```

`df1`を`df2`から結合された列で更新することによって、2つのデータフレームオブジェクトの左結合を実行します。

左結合には`df1`のすべての行が含まれ、`df1`のすべての行と列は変更されません。`df1`の各行は`df2`において最大1つの一致を持つ必要があります。そうでない場合、この関数は新しい行を`df1`に追加する必要があるため、インプレースで結合を実行できません。

# 引数

  * `df1`, `df2`: 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するためのキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合するため）であることができます。`df1`と`df2`でキーの名前が異なる場合は、名前のペア`left=>right`を使用することができます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `false`（デフォルト）の場合、結合されていない列に重複した名前が見つかった場合にエラーが発生します。`true`の場合、重複した名前には`_i`（最初の重複のために`i`は1から始まる）が接尾辞として付加されます。
  * `source` : デフォルト: `nothing`。`Symbol`または文字列の場合、行が`df1`のみに存在するか（`"left_only"`）、両方に存在するか（`"both"`）を示す指定された名前のインジケーター列を追加します。名前がすでに使用されている場合、`makeunique=true`の場合は列名が変更されます。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合にエラーをスローします。`:equal`に等しい場合、`missing`が許可され、欠損値が一致します。`:notequal`に等しい場合、`df2`の`on`列の欠損値は削除されます。

`df2`から`df1`に追加される列は、欠損値をサポートします。

`NaN`または`-0.0`を含む列での結合は許可されていません。これらの値で結合を行う必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

メタデータ: テーブルレベルおよび列レベルの`:note`スタイルのメタデータは、`df1`から取得されます（キー列を含む）、`df2`から追加された列の列レベルの`:note`スタイルのメタデータは`df2`から取得されます。

参照: [`leftjoin`](@ref)。

# 例

```jldoctest
julia> name = DataFrame(ID=[1, 2, 3], Name=["John Doe", "Jane Doe", "Joe Blogs"])
3×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     1  John Doe
   2 │     2  Jane Doe
   3 │     3  Joe Blogs

julia> job = DataFrame(ID=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ ID     Job
     │ Int64  String
─────┼───────────────
   1 │     1  Lawyer
   2 │     2  Doctor
   3 │     4  Farmer

julia> leftjoin!(name, job, on = :ID)
3×3 DataFrame
 Row │ ID     Name       Job
     │ Int64  String     String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> leftjoin!(name, job2, on = :ID => :identifier, makeunique=true, source=:source)
3×5 DataFrame
 Row │ ID     Name       Job      Job_1    source
     │ Int64  String     String?  String?  String
─────┼───────────────────────────────────────────────
   1 │     1  John Doe   Lawyer   Lawyer   both
   2 │     2  Jane Doe   Doctor   Doctor   both
   3 │     3  Joe Blogs  missing  missing  left_only
```
