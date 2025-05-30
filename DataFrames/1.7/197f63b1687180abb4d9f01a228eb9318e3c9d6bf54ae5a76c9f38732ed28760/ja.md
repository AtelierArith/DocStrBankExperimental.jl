```
leftjoin(df1, df2; on, makeunique=false, source=nothing, validate=(false, false),
         renamecols=(identity => identity), matchmissing=:error, order=:undefined)
```

2つのデータフレームオブジェクトを左結合し、結果を含む`DataFrame`を返します。左結合には`df1`のすべての行が含まれます。

返されるデータフレームでは、データフレームが結合される列の型は`df1`のこれらの列の型によって決定されます。この動作は将来のリリースで変更される可能性があります。

# 引数

  * `df1`, `df2`: 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するためのキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合するため）であることができます。キーが`df1`と`df2`で異なる名前を持つ場合は、名前のペア`left=>right`を使用できます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `false`（デフォルト）の場合、結合されていない列に重複した名前が見つかった場合にエラーが発生します。`true`の場合、重複した名前には`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。
  * `source` : デフォルト: `nothing`。`Symbol`または文字列の場合、行が`df1`のみに現れたか（`"left_only"`）、両方に現れたか（`"both"`）を示すインジケーター列が追加されます。名前がすでに使用されている場合、`makeunique=true`のときに列名が変更されます。
  * `validate` : `on`引数として渡された列が各入力データフレームで一意のキーを定義しているかどうかを確認するかどうか。タプルまたはペアで指定でき、最初の要素が`df1`のチェックを実行するかどうか、2番目の要素が`df2`のチェックを実行するかどうかを示します。デフォルトではチェックは行われません。
  * `renamecols` : 左右のデータフレームの列が結果のデータフレームでどのように名前を変更されるかを指定する`Pair`。ペアの各要素は文字列または`Symbol`であることができ、その場合は元の列名に追加されます。あるいは、関数を渡すこともでき、その場合は各列名に適用され、列名は`String`として渡されます。`renamecols`は`on`列には影響せず、その名前は常に左のデータフレームから取得され、変更されません。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合にエラーをスローします。`:equal`に等しい場合、`missing`が許可され、欠損値が一致します。`:notequal`に等しい場合、`df2`の`on`列の欠損値は削除されます。
  * `order` : `:undefined`（デフォルト）の場合、結果の行の順序は未定義であり、将来のリリースで変更される可能性があります。`:left`の場合、左のデータフレームからの行の順序が保持されます。`:right`の場合、右のデータフレームからの行の順序が保持されます（一致しない行は最後に配置されます）。

返されるデータフレームのすべての列は欠損値をサポートします。

`NaN`または`-0.0`を含む列で結合することは許可されていません。これらの値で結合を行う必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

レベルの順序が異なる`on`カテゴリカル列をマージする場合、左のデータフレームの順序が右のデータフレームの順序に優先します。

メタデータ: テーブルレベルおよび列レベルの`:note`スタイルのメタデータは`df1`から取得されます（キー列を含む）、`df2`から追加された列については、列レベルの`:note`スタイルのメタデータは`df2`から取得されます。

参照: [`innerjoin`](@ref), [`rightjoin`](@ref), [`outerjoin`](@ref),           [`semijoin`](@ref), [`antijoin`](@ref), [`crossjoin`](@ref).

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

julia> leftjoin(name, job, on = :ID)
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

julia> leftjoin(name, job2, on = :ID => :identifier, renamecols = "_left" => "_right")
3×3 DataFrame
 Row │ ID     Name_left  Job_right
     │ Int64  String     String?
─────┼─────────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing

julia> leftjoin(name, job2, on = [:ID => :identifier], renamecols = uppercase => lowercase)
3×3 DataFrame
 Row │ ID     NAME       job
     │ Int64  String     String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing
```
