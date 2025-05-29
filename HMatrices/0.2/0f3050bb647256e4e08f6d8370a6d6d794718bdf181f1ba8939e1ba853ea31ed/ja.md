```
struct PartialACA
```

部分ピボットを用いた適応交差近似アルゴリズム。この構造体は、行列のようなオブジェクト `M` から [`RkMatrix`](@ref) を生成するために使用できます。以下のように：

```jldoctest
using LinearAlgebra
rtol = 1e-6
comp = PartialACA(;rtol)
A = rand(10,2)
B = rand(10,2)
M = A*adjoint(B) # 低ランク行列
R = comp(M, axes(M)...) # 行列 `M` 全体を圧縮
norm(Matrix(R) - M) < rtol*norm(M) # 真

# 出力

true

```

部分ピボットを使用するため、線形演算子はすべての `i,j` で評価される必要はありません。これは通常、[`TSVD`](@ref) よりもはるかに速いですが、ピボット戦略のため、基になる線形演算子が低ランクであっても、特別な場合にアルゴリズムが失敗する可能性があります。
