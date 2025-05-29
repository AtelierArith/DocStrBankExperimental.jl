```
writefame(db, data; options)
```

FAMEデータベースにJuliaデータを書き込みます。

### 引数:

  * `db` はFAME .dbファイルへのパスを含む文字列または[`FameDatabase`](@ref)のインスタンスです。
  * `data` はデータベースに書き込まれるデータのコレクションです。

      * `data` が `MVTSeries` の場合、各シリーズがデータベースに書き込まれます。
      * `data` が `Workspace` の場合、各要素が別々のFAMEオブジェクトとして書き込まれます。この場合、ネストされた `Workspace` の `MVTSeries` オブジェクトは名前を前に付けて再帰的に書き込まれます。

### オプション:

  * `mode::Symbol` - `db` が文字列の場合、指定された `mode` でデータベースが開かれます。デフォルトは :overwrite です。
  * `prefix::Union{Nothing,String}` - 指定された `prefix` はデータベースに書き込まれる各オブジェクトの名前の前に付けられます。デフォルトは `nothing` で、つまり何も前に付けられません。注意: `prefix=nothing` と `prefix=""` は同じではありません。
  * `glue::String` - `glue` はプレフィックスと名前を結合するために使用されます。デフォルトは `"_"` です。

### 例:

```
julia> w = Workspace(; a=1, b=TSeries(2020Q1,ones(10)), s=MVTSeries(2020M1, collect("ab"), randn(24,2)))
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  s ⇒ 24×2 MVTSeries{Monthly} with range 2020M1:2021M12 and variables …

julia> writefame("w.db", w)

julia> listdb("w.db")
2-element Vector{FAME.FameObject}:
 A: scalar,precision,undefined,0:0,0:0
 B: series,precision,quarterly_december,2020:1,2022:2
 S_A: series,precision,monthly,2020:1,2021:12
 S_B: series,precision,monthly,2020:1,2021:12

```
