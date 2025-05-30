```
semijoin(df1, df2; on, makeunique=false, validate=(false, false), matchmissing=:error)
```

2つのデータフレームオブジェクトのセミジョインを実行し、結果を含む`DataFrame`を返します。セミジョインは、`df1`の行のサブセットを返し、`df2`のキーと一致します。

結果の行の順序は`df1`から保持されます。

# 引数

  * `df1`, `df2`: 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合する場合）であることができます。キーが`df1`と`df2`で異なる名前を持つ場合、名前のペア`left=>right`を使用することができます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `df1`の列に列が追加されないため無視されます（他の関数との一貫性のために提供されています）。
  * `indicator` : デフォルト: `nothing`。`Symbol`または文字列の場合、行が`df1`にのみ出現したか（`"left_only"`）、`df2`にのみ出現したか（`"right_only"`）、または両方に出現したか（`"both"`）を示す指定された名前のカテゴリカルインジケーター列を追加します。名前がすでに使用されている場合、`makeunique=true`の場合は列名が変更されます。
  * `validate` : `on`引数として渡された列が各入力データフレームで一意のキーを定義しているかどうかを確認するかどうか（`isequal`に従って）。タプルまたはペアであり、最初の要素が`df1`のチェックを実行するかどうか、2番目の要素が`df2`のチェックを実行するかどうかを示します。デフォルトではチェックは実行されません。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合はエラーをスローします。`:equal`に等しい場合、`missing`が許可され、欠損値が一致します。`:notequal`に等しい場合、`df2`の`on`列の欠損値は削除されます。

実数または虚数の部分に`NaN`または`-0.0`を含む列で結合することは許可されていません。そのような値で結合を実行する必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

レベルの順序が異なるカテゴリカル列で`on`をマージする場合、左のデータフレームの順序が右のデータフレームの順序に優先します。

メタデータ: テーブルレベルおよび列レベルの`:note`スタイルのメタデータは`df1`から取得されます。

参照: [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`outerjoin`](@ref), [`antijoin`](@ref), [`crossjoin`](@ref).

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

julia> semijoin(name, job, on = :ID)
2×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼─────────────────
   1 │     1  John Doe
   2 │     2  Jane Doe

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> semijoin(name, job2, on = :ID => :identifier)
2×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼─────────────────
   1 │     1  John Doe
   2 │     2  Jane Doe

julia> semijoin(name, job2, on = [:ID => :identifier])
2×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼─────────────────
   1 │     1  John Doe
   2 │     2  Jane Doe
```
