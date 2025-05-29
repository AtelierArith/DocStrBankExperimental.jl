```
mwearray([io::IO=stdout], t::AbstractVector; name=:x)
```

`Vector`から最小限の作業例（MWE）を作成します。`mwearray`は`t`を再作成するために必要なコードを含む複数行の文字列を返します。デフォルトでは`stdout`に出力します。

# 例

```julia-repl
julia> mwearray(x; name=:x)
x = """
1
2
3
4
""" |> IOBuffer |> CSV.File |> Tables.matrix |> vec
```
