```
innerjoin(df1, df2; on, makeunique=false, validate=(false, false),
          renamecols=(identity => identity), matchmissing=:error,
          order=:undefined)
innerjoin(df1, df2, dfs...; on, makeunique=false,
          validate=(false, false), matchmissing=:error,
          order=:undefined)
```

2つ以上のデータフレームオブジェクトの内部結合を実行し、結果を含む`DataFrame`を返します。内部結合には、すべての渡されたデータフレームで一致するキーを持つ行が含まれます。

返されるデータフレームでは、データフレームが結合される列の型は`df1`のこれらの列の型によって決まります。この動作は将来のリリースで変更される可能性があります。

# 引数

  * `df1`, `df2`, `dfs...`: 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するためのキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合するため）であることができます。2つのデータフレームのみを結合する場合、`left=>right`の名前のペアを名前の代わりに使用することができ、`df1`と`df2`でキーが異なる名前を持つ場合に使用されます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `false`（デフォルト）の場合、結合されていない列に重複した名前が見つかった場合にエラーが発生します。`true`の場合、重複した名前には`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。
  * `validate` : `on`引数として渡された列が各入力データフレームで一意のキーを定義しているかどうかを確認するかどうか。タプルまたはペアであり、最初の要素が`df1`のチェックを実行するかどうかを示し、2番目の要素が`df2`のためのものです。デフォルトではチェックは行われません。
  * `renamecols` : 左側と右側のデータフレームの列が結果のデータフレームでどのように名前を変更されるべきかを指定する`Pair`。ペアの各要素は文字列または`Symbol`であり、元の列名に追加されます。あるいは、関数を渡すこともでき、その場合は各列名に適用され、`String`として渡されます。`renamecols`は`on`列には影響を与えず、その名前は常に左側のデータフレームから取得され、変更されません。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合にエラーをスローします。`:equal`に等しい場合、`missing`が許可され、欠損値が一致します。`:notequal`に等しい場合、`df1`と`df2`の`on`列の欠損値は削除されます。
  * `order` : `:undefined`（デフォルト）の場合、結果の行の順序は未定義であり、将来のリリースで変更される可能性があります。`:left`の場合、左側のデータフレームの行の順序が保持されます。`:right`の場合、右側のデータフレームの行の順序が保持されます。

`NaN`または`-0.0`を含む列で結合することは許可されていません。これらの値で結合を行う必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

レベルの順序が異なる`on`カテゴリカル列をマージする場合、左側のデータフレームの順序が右側のデータフレームの順序に優先します。

2つ以上のデータフレームが渡された場合、結合は左結合的に再帰的に行われます。この場合、`validate`キーワード引数は左結合的に再帰的に適用されます。

メタデータ：テーブルレベルの`:note`スタイルのメタデータと列レベルの`:note`スタイルのメタデータは、すべての渡されたテーブルで定義され、同じ値を持つキーに対してのみ保持されます。列レベルの`:note`スタイルのメタデータは、他のすべての列に対して保持されます。

参照：[`leftjoin`](@ref)、[`rightjoin`](@ref)、[`outerjoin`](@ref)、           [`semijoin`](@ref)、[`antijoin`](@ref)、[`crossjoin`](@ref)。

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

julia> innerjoin(name, job, on = :ID)
2×3 DataFrame
 Row │ ID     Name      Job
     │ Int64  String    String
─────┼─────────────────────────
   1 │     1  John Doe  Lawyer
   2 │     2  Jane Doe  Doctor

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> innerjoin(name, job2, on = :ID => :identifier, renamecols = "_left" => "_right")
2×3 DataFrame
 Row │ ID     Name_left  Job_right
     │ Int64  String     String
─────┼─────────────────────────────
   1 │     1  John Doe   Lawyer
   2 │     2  Jane Doe   Doctor

julia> innerjoin(name, job2, on = [:ID => :identifier], renamecols = uppercase => lowercase)
2×3 DataFrame
 Row │ ID     NAME      job
     │ Int64  String    String
─────┼─────────────────────────
   1 │     1  John Doe  Lawyer
   2 │     2  Jane Doe  Doctor
```
