forwardrecurrence(N, A, B, C, x)

は、点 `x` で最初の `N` 個の直交多項式を評価します。ここで、`A`、`B`、および `C` は、[DLMF](https://dlmf.nist.gov/18.9) で定義された最初の形式の再帰係数を含む `AbstractVector` です。すなわち、i = 0, 1, ..., N-1 に対して Pᵢ(x) を返します。
