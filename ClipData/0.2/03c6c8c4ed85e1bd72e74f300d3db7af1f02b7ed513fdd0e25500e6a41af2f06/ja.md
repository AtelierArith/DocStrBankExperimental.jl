```
mwetable([io::IO=stdout], t; name="df")
```

既存のTables.jl互換オブジェクトから最小限の作業例（MWE）を作成します。`tablmwe`は、複数行のカンマ区切り文字列を出力し、その文字列を`CSV.File`を使用して読み込むために必要なコードを提供します。オブジェクトは、`name`（デフォルトは`:df`）で指定された名前が付けられます。出力は`io`に行われ、デフォルトでは`stdout`です。

# 例

```julia-repl
julia> t = (a = [1, 2, 3], b = [100, 200, 300])
(a = [1, 2, 3], b = [100, 200, 300])

julia> mwetable(t)
df = """
a,b
1,100
2,200
3,300
""" |> IOBuffer |> CSV.File
```
