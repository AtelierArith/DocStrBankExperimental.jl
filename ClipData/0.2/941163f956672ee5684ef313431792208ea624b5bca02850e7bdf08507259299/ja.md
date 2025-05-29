```
@mwetable(t)
```

既存のTables.jl互換オブジェクトから最小限の作業例（MWE）を作成します。`tablmwe`は、複数行のカンマ区切り文字列を出力し、その文字列を`CSV.File`を使用して読み取るために必要なコードを提供します。MWE内でオブジェクトに割り当てられる名前は、入力オブジェクトの名前と同じです。`stdout`に出力します。

# 例

```julia-repl
julia> my_special_table = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> @mwetable my_special_table
my_special_table = """
a,b
1,100
2,200
3,300
""" |> IOBuffer |> CSV.File
```
