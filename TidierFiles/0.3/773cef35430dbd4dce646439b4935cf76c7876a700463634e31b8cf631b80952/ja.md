```
function read_dta(data_file;  encoding=nothing, col_select=nothing, skip=0, n_max=Inf)
```

Stata (.dta) ファイルからデータを DataFrame に読み込み、ローカルおよびリモートソースの両方をサポートします。

# 引数

  * `filepath`: .dta ファイルへのパスまたはそのようなファイルを指す URL。URL が提供されると、ファイルはダウンロードされてから読み込まれます。

`encoding`: オプション; 入力ファイルのエンコーディングを指定します。提供されない場合は、パッケージまたは関数のデフォルトに従います。 `col_select`: オプション; 読み込む列のサブセットを指定できます。これは列名またはインデックスのベクターです。何も指定しない場合は、すべての列が読み込まれます。

  * `skip=0`: 読み込み前にスキップするファイルの先頭の行数。
  * `n_max=Inf`: スキップ後にファイルから読み込む最大行数。Inf の場合、利用可能なすべての行を読み込みます。

`num_threads`: 処理に使用する同時タスクまたはスレッドの数を指定し、並列実行を可能にします。デフォルトは 1 です。

# 例

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_dta(df, "test.dta");

julia> read_dta("test.dta")
2×2 DataFrame
 Row │ AA       AB      
     │ String3  Float64 
─────┼──────────────────
   1 │ sav         10.1
   2 │ por         10.2
```
