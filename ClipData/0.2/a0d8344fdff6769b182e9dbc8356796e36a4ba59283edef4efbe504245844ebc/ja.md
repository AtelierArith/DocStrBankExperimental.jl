```
@mwearray(t)
```

`Vector` または `Matrix` から、Julia セッション内のオブジェクトと同じ名前の最小作業例 (MWE) を作成します。`stdout` に出力します。

# 例

```julia-repl
julia> my_special_matrix = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> @mwearray my_special_matrix
my_special_matrix = """
1,2
3,4
""" |> IOBuffer |> CSV.File |> Tables.matrix
```
