```
mwearray([io::IO=stdout], t::AbstractMatrix; name=:X)
```

`Matrix`から最小限の作業例（MWE）を作成します。`mwearray`は`t`を再作成するために必要なコードを含む複数行の文字列を返します。デフォルトでは`stdout`に出力します。

# 例

```julia-repl
julia> X = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mwearray(X)
X = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
