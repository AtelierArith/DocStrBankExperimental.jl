```
write_table(x, file; delim = '	', na, append, col_names, eol, num_threads)
```

DataFrameをファイルに書き込み、区切り文字やその他のオプションをカスタマイズできるようにします。

# 引数

  * `x`: ファイルに書き込むDataFrame。
  * `file`: DataFrameが書き込まれるファイルのパス。

-delim: フィールド区切り文字として使用する文字。デフォルトはタブ（'	'）で、デフォルトではTSV（タブ区切り値）ファイルになりますが、他の形式に合わせて変更できます。

  * `missing_value`: 出力ファイル内の欠損データを表す文字列。
  * `append`: ファイルが既に存在する場合に追加するかどうか。falseの場合、ファイルは上書きされます。
  * `col_names`: ファイルの最初の行に列名を書き込むかどうか。append = trueで既存のファイルに追加する場合、このパラメータの値に関係なく列名は書き込まれません。
  * `eol`: ファイル内で使用する行末文字。デフォルトは"

"です。

  * `num_threads`: ファイルを書き込むために使用するスレッドの数。デフォルトでは利用可能なJuliaスレッドの数を使用します。

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_table(df, "tabletest.txt");
```
