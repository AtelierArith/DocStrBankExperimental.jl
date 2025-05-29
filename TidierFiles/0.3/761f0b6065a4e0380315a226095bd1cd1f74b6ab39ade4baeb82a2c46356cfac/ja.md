```
read_csv(file; delim=',',col_names=true, skip=0, n_max=Inf, 
    comment=nothing, missing_value="", col_select, escape_double=true, col_types=nothing, num_threads = 1)
```

CSVファイルまたはURLをDataFrameに読み込み、区切り文字、列名、およびその他のCSV解析オプションを指定するためのオプションがあります。

# 引数

  * `file`: CSVファイルへのパスまたはパスのベクター、またはCSVファイルへのURL。
  * `delim`: ファイル内のフィールドを区切る文字。デフォルトは','です。
  * `decimal`: 小数点として使用する文字の文字引数。デフォルトは`.`です。
  * `col_names`: CSVの最初の行が列名として使用されるかどうかを示します。true、false、または文字列の配列を指定できます。デフォルトはtrueです。
  * `skip`: データを読み込む前にスキップする初期行の数。デフォルトは0です。
  * `n_max`: 読み込む最大行数。デフォルトはInf（すべての行を読み込む）です。
  * `col_select`: 読み込む列を選択するためのオプションのシンボルまたは文字列のベクター。
  * `col_types`: 列の型を指定するためのオプションのDict
  * `comment`: コメント行を開始する文字。これに続く文字で始まる行は無視されます。デフォルトはnothing（コメント行なし）です。
  * `missing_value`: CSV内の欠損値を表す文字列。デフォルトは""で、複数のアイテムのベクターに設定できます。
  * `escape_double`: 2つの連続した引用符をデータ内の単一の引用符として解釈するかどうかを示します。デフォルトはtrueです。
  * `num_threads`: 処理に使用する同時タスクまたはスレッドの数を指定し、並列実行を可能にします。デフォルトは1です。

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_csv(df, "csvtest.csv");

julia> read_csv("csvtest.csv", skip = 2, n_max = 3, missing_value = ["95", "Charlie"])
3×3 DataFrame
 Row │ ID     Name      Score   
     │ Int64  String7?  Int64?  
─────┼──────────────────────────
   1 │     3  missing        77
   2 │     4  David          85
   3 │     5  Eva       missing 

julia> read_csv("csvtest.csv", skip = 2, n_max = 3, col_types = Dict(:ID => Float64))
3×3 DataFrame
 Row │ ID       Name     Score 
     │ Float64  String7  Int64 
─────┼─────────────────────────
   1 │     3.0  Charlie     77
   2 │     4.0  David       85
   3 │     5.0  Eva         95
```
