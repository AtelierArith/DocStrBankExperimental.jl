```
antijoin(df1, df2; on, makeunique=false, validate=(false, false), matchmissing=:error)
```

2つのデータフレームオブジェクトのアンチジョインを実行し、結果を含む`DataFrame`を返します。アンチジョインは、`df1`の中で`df2`のキーと一致しない行のサブセットを返します。

結果の行の順序は`df1`から保持されます。

# 引数

  * `df1`, `df2`: 結合される`AbstractDataFrames`

# キーワード引数

  * `on` : データフレームを結合するためのキー列の名前。これは単一の名前、または名前のベクター（複数の列で結合するため）であることができます。キーが`df1`と`df2`で異なる名前を持つ場合は、名前のペア`left=>right`を使用することができます（ベクター内で名前と名前のペアを混在させることが許可されています）。キー値は`isequal`を使用して比較されます。`on`は必須の引数です。
  * `makeunique` : `df1`の列に列が追加されないため無視されます（他の関数との一貫性のために提供されています）。
  * `validate` : `on`引数として渡された列が各入力データフレームでユニークなキーを定義しているかどうかをチェックするかどうか（`isequal`に従って）。タプルまたはペアで、最初の要素が`df1`のチェックを実行するかどうか、2番目の要素が`df2`のチェックを実行するかどうかを示します。デフォルトではチェックは行われません。
  * `matchmissing` : `:error`に等しい場合、`on`列に`missing`が存在する場合はエラーをスローします；`:equal`に等しい場合、`missing`が許可され、欠損値が一致します；`:notequal`に等しい場合、`df2`の`on`列の欠損値は削除されます。

`NaN`または`-0.0`を含む列で結合することは許可されていません。これらの値で結合を行う必要がある場合は、CategoricalArrays.jlを使用し、そのような値を含む列を`CategoricalVector`に変換してください。

レベルの順序が異なるカテゴリカル列を`on`でマージする場合、左側のデータフレームの順序が右側のデータフレームの順序に優先します。

メタデータ：テーブルレベルおよび列レベルの`:note`スタイルのメタデータは`df1`から取得されます。

参照： [`innerjoin`](@ref), [`leftjoin`](@ref), [`rightjoin`](@ref),           [`outerjoin`](@ref), [`semijoin`](@ref), [`crossjoin`](@ref).

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

julia> antijoin(name, job, on = :ID)
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs

julia> job2 = DataFrame(identifier=[1, 2, 4], Job=["Lawyer", "Doctor", "Farmer"])
3×2 DataFrame
 Row │ identifier  Job
     │ Int64       String
─────┼────────────────────
   1 │          1  Lawyer
   2 │          2  Doctor
   3 │          4  Farmer

julia> antijoin(name, job2, on = :ID => :identifier)
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs

julia> antijoin(name, job2, on = [:ID => :identifier])
1×2 DataFrame
 Row │ ID     Name
     │ Int64  String
─────┼──────────────────
   1 │     3  Joe Blogs
```
