```
read_delim(file; delim='	',col_names=true, skip=0, n_max=Inf, 
    comment=nothing, missing_value="", col_select, escape_double=true, col_types=nothing)
```

区切り文字付きファイルまたはURLをDataFrameに読み込み、区切り文字、列名、およびその他のCSV解析オプションを指定するオプションがあります。

# 引数

  * `file`: CSVファイルへのパスまたはパスのベクター、またはCSVファイルへのURL。
  * `delim`: ファイル内のフィールドを区切る文字。デフォルトは','。
  * `decimal`: 小数点として使用する文字の引数。デフォルトは`.`。
  * `col_names`: CSVの最初の行が列名として使用されるかどうかを示します。true、false、または文字列の配列を指定できます。デフォルトはtrue。
  * `skip`: データを読み込む前にスキップする初期行の数。デフォルトは0。
  * `n_max`: 読み込む最大行数。デフォルトはInf（すべての行を読み込む）。
  * `col_select`: 読み込む列を選択するためのオプションのシンボルまたは文字列のベクター。
  * `comment`: コメント行を開始する文字。これに続く文字で始まる行は無視されます。デフォルトはnothing（コメント行なし）。
  * `col_types`: 列の型を指定するためのオプションのDict。
  * `missing_value`: CSV内の欠損値を表す文字列。デフォルトは""、複数のアイテムのベクターに設定できます。
  * `escape_double`: 2つの連続した引用符をデータ内の単一の引用符として解釈するかどうかを示します。デフォルトはtrue。
  * `num_threads`: 処理に使用する同時タスクまたはスレッドの数を指定し、並列実行を可能にします。デフォルトは利用可能なスレッドの数です。

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_csv(df, "csvtest.csv");

julia> read_delim("csvtest.csv", delim = ",", col_names = false, num_threads = 4) # col_namesはデモの目的でここではfalseです
6×3 DataFrame
 Row │ Column1  Column2  Column3 
     │ String3  String7  String7 
─────┼───────────────────────────
   1 │ ID       Name     Score
   2 │ 1        Alice    88
   3 │ 2        Bob      92
   4 │ 3        Charlie  77
   5 │ 4        David    85
   6 │ 5        Eva      95
```
