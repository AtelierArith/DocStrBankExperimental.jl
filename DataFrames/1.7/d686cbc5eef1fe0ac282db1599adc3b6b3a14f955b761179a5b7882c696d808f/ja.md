```
outerjoin(df1, df2; on, makeunique=false, source=nothing, validate=(false, false),
          renamecols=(identity => identity), matchmissing=:error, order=:undefined)
outerjoin(df1, df2, dfs...; on, makeunique = false,
          validate = (false, false), matchmissing=:error, order=:undefined)
```

2つ以上のデータフレームオブジェクトの外部結合を実行し、結果を含む`DataFrame`を返します。外部結合には、渡されたデータフレームのいずれかに出現するキーを持つ行が含まれます。

結果の行の順序は未定義であり、将来のリリースで変更される可能性があります。

返されるデータフレームでは、データフレームが結合される列の型は、`df1`と`df2`のこれらの列の要素型によって決定されます。この動作は将来のリリースで変更される可能性があります。

# 引数

  * `df1`, `df2`, `dfs...` : 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するためのキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合するため）であることができます。2つのデータフレームのみを結合する場合、`df1`と`df2`でキーが異なる名前の場合に、名前のペア`left=>right`を使用することができます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `false`（デフォルト）の場合、結合されていない列に重複した名前が見つかった場合にエラーが発生します。`true`の場合、重複した名前には`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。
  * `source` : デフォルト: `nothing`。`Symbol`または文字列の場合、行が`df1`（`"left_only"`）、`df2`（`"right_only"`）のいずれかにのみ出現したか、または両方に出現したかを示すインジケーター列を追加します。名前がすでに使用されている場合、`makeunique=true`の場合は列名が変更されます。この引数は、正確に2つのデータフレームを結合する場合にのみサポートされています。
  * `validate` : `on`引数として渡された列が各入力データフレームで一意のキーを定義しているかどうかを確認するかどうか。タプルまたはペアであり、最初の要素は`df1`のチェックを実行するかどうか、2番目の要素は`df2`のチェックを実行するかどうかを示します。デフォルトではチェックは実行されません。
  * `renamecols` : 左右のデータフレームの列が結果のデータフレームでどのように名前を変更されるべきかを指定する`Pair`。ペアの各要素は文字列または`Symbol`であり、元の列名に追加されます。あるいは、関数を渡すこともでき、その場合は各列名に適用され、`String`として渡されます。`renamecols`は`on`列には影響せず、その名前は常に左のデータフレームから取得され、変更されません。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合はエラーをスローします。`:equal`に等しい場合、`missing`が許可され、欠損値が一致します。
  * `order` : `:undefined`（デフォルト）の場合、結果の行の順序は未定義であり、将来のリリースで変更される可能性があります。`:left`の場合、左のデータフレームからの行の順序が保持されます（一致しない行は最後に配置されます）。`:right`の場合、右のデータフレームからの行の順序が保持されます（一致しない行は最後に配置されます）。

返されるデータフレームのすべての列は、欠損値をサポートします。

`NaN`または`-0.0`を含む列で結合することは許可されていません。これらの値で結合を行う必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

レベルの順序が異なる`on`カテゴリカル列をマージする場合、左のデータフレームの順序が右のデータフレームの順序に優先します。

2つ以上のデータフレームが渡された場合、結合は左結合的に再帰的に実行されます。この場合、`indicator`キーワード引数はサポートされず、`validate`キーワード引数は左結合的に再帰的に適用されます。

メタデータ: テーブルレベルの`:note`スタイルのメタデータと列レベルの`:note`スタイルのメタデータは、すべての渡されたテーブルで定義され、同じ値を持つキーに対してのみ保持されます。列レベルの`:note`スタイルのメタデータは、他のすべての列に対して保持されます。

参照: [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`semijoin`](@ref), [`antijoin`](@ref), [`crossjoin`](@ref)。

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

julia> outerjoin(name, job, on = :ID)
4×3 DataFrame
 Row │ ID     Name       Job
     │ Int64  String?    String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing
   4 │     4  missing    Farmer

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> outerjoin(name, job2, on = :ID => :identifier, renamecols = "_left" => "_right")
4×3 DataFrame
 Row │ ID     Name_left  Job_right
     │ Int64  String?    String?
─────┼─────────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing
   4 │     4  missing    Farmer

julia> outerjoin(name, job2, on = [:ID => :identifier], renamecols = uppercase => lowercase)
4×3 DataFrame
 Row │ ID     NAME       job
     │ Int64  String?    String?
─────┼───────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor
   3 │     3  Joe Blogs  missing
   4 │     4  missing    Farmer
```
