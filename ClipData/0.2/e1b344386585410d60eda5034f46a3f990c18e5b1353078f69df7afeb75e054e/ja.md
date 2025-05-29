```
mwetable([io::IO=stdout]; name="df")
```

クリエイト最小作業例 (MWE) をクリップボードを使用して作成します。 `tablmwe` は複数行のカンマ区切り文字列を出力し、その文字列を `CSV.File` を使用して読み取るために必要なコードを提供します。オブジェクトは `name` で指定された名前（デフォルトは `"df"`）が割り当てられます。デフォルトでは `stdout` に出力します。

# 例

```julia-repl
julia> """
       a b
       1 2
       100 200
       """ |> clipboard

julia> mwetable()
df = """
a,b
1,2
100,200
""" |> IOBuffer |> CSV.File
```
