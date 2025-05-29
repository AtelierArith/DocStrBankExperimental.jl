```
read_table(file; col_names=true, skip=0, n_max=Inf, comment=nothing, col_select, missing_value="", kwargs...)
```

ファイルからテーブルを読み込み、列が任意の量の空白で区切られている場合、DataFrameに処理します。

# 引数

  * `file`: 読み込むファイルのパス。
  * `col_names`=true: 最初の非スキップ行を列名として扱うかどうかを示します。falseの場合、列は自動的に名前が付けられます。
  * `skip`: 処理を開始する前にスキップするファイルの先頭の行数。
  * `n_max`: スキップ後にファイルから読み込む最大行数。Infはすべての行を読み込むことを意味します。
  * `col_select`: 読み込む列を選択するためのオプションのシンボルまたは文字列のベクター。
  * `comment`: コメントの開始を示す文字または文字列。これらの文字で始まる行は無視されます。
  * `missing_value`: テーブル内の欠損値を表す文字列。
  * `kwargs`: CSV.Fileに渡される追加のキーワード引数。

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_table(df, "tabletest.txt");

julia> read_table("tabletest.txt", skip = 2, n_max = 3, col_select = ["Name"])
3×1 DataFrame
 Row │ Name    
     │ String7 
─────┼─────────
   1 │ Charlie
   2 │ David
   3 │ Eva

```
