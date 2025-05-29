```
mwearray([io::IO=stdout]; name=:X)
```

クリップボードから配列を作成する最小限の作業例（MWE）を作成します。`mwearray`は、クリップボードに保存された文字列を`Vector`または`Matrix`として読み取るために必要なコードを含むマルチライン文字列を返します。デフォルトでは`stdout`に出力します。

# 例

```julia-repl
julia> """
       1 2
       3 4
       """ |> clipboard

julia> mwearray()
X = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
