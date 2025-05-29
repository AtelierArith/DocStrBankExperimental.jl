forwardrecurrence(A, B, C, x)

は、点 `x` で最初の `N+1` 個の直交多項式を評価します。ここで、`A`、`B`、および `C` は、[DLMF](https://dlmf.nist.gov/18.9) で定義された最初の形式の再帰係数を含む `AbstractVector` であり、`N` は `A`、`B`、および `C` の最小長さです。つまり、i = 0, 1, ..., `min(length(A), length(B), length(C))` に対して Pᵢ(x) を返します。
