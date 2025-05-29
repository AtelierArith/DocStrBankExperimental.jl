```
function read_sav(data_file;  encoding=nothing, col_select=nothing, skip=0, n_max=Inf)
```

SPSS（.savおよび.por）ファイルからデータをDataFrameに読み込み、ローカルおよびリモートソースの両方をサポートします。

# 引数

  * `filepath`: .savまたは.porファイルへのパス、またはそのようなファイルを指すURL。URLが提供されると、ファイルはダウンロードされてから読み込まれます。
  * `encoding`: オプション; 入力ファイルのエンコーディングを指定します。指定しない場合は、パッケージまたは関数のデフォルトに従います。
  * `col_select`: オプション; 読み込む列のサブセットを指定できます。これは列名またはインデックスのベクターです。何も指定しない場合は、すべての列が読み込まれます。
  * `skip=0`: 読み込み前にファイルの先頭からスキップする行数。
  * `n_max=Inf``: スキップ後にファイルから読み込む最大行数。Infの場合、利用可能なすべての行を読み込みます。
  * `num_threads`: 処理に使用する同時タスクまたはスレッドの数を指定し、並列実行を可能にします。デフォルトは1です。

# 例

```jldoctest
julia> df = DataFrame(AA=["sav", "por"], AB=[10.1, 10.2]);

julia> write_sav(df, "test.sav");

julia> read_sav("test.sav")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ sav        10.1
   2 │ por        10.2

julia> write_sav(df, "test.por");

julia> read_sav("test.por")
2×2 DataFrame
 Row │ AA      AB      
     │ String  Float64 
─────┼─────────────────
   1 │ sav        10.1
   2 │ por        10.2
```
