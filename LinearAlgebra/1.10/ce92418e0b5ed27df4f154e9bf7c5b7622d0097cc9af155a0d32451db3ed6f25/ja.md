```
lu(A, pivot = RowMaximum(); check = true) -> F::LU
```

行列 `A` の LU 分解を計算します。

`check = true` の場合、分解が失敗した場合にエラーがスローされます。`check = false` の場合、分解の有効性を確認する責任はユーザーにあります（[`issuccess`](@ref) を介して）。

ほとんどの場合、`A` が要素型 `T` を持ち、`+`、`-`、`*`、および `/` をサポートする `AbstractMatrix{T}` のサブタイプ `S` である場合、戻り値の型は `LU{T,S{T}}` です。

一般に、LU 分解は行列の行の順序を入れ替えることを含みます（以下に説明する `F.p` 出力に対応）、これは「ピボッティング」と呼ばれます（なぜなら、これは「ピボット」、すなわち `F.U` の対角成分を含む行を選択することに対応するからです）。次のいずれかのピボッティング戦略をオプションの `pivot` 引数を介して選択できます：

  * `RowMaximum()`（デフォルト）：標準的なピボッティング戦略；ピボットは、残りの分解される行の中で最大の絶対値を持つ要素に対応します。このピボッティング戦略は、要素型が [`abs`](@ref) および [`<`](@ref) をサポートすることを要求します。（これは一般に浮動小数点行列に対して唯一の数値的に安定したオプションです。）
  * `RowNonZero()`：ピボットは、残りの分解される行の中で最初の非ゼロ要素に対応します。（これは手計算での典型的な選択に対応し、[`iszero`](@ref) をサポートするが `abs` や `<` をサポートしないより一般的な代数数型にも便利です。）
  * `NoPivot()`：ピボッティングをオフにします（ゼロエントリに遭遇した場合に失敗する可能性があります）。

分解 `F` の個々のコンポーネントには [`getproperty`](@ref) を介してアクセスできます：

| コンポーネント | 説明                |
|:------- |:----------------- |
| `F.L`   | `LU` の `L`（下三角）部分 |
| `F.U`   | `LU` の `U`（上三角）部分 |
| `F.p`   | （右）置換 `Vector`    |
| `F.P`   | （右）置換 `Matrix`    |

分解を反復することで、コンポーネント `F.L`、`F.U`、および `F.p` を得ることができます。

`F` と `A` の関係は次の通りです。

`F.L*F.U == A[F.p, :]`

`F` はさらに次の関数をサポートします：

| サポートされる関数           | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

# 例

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # 反復を介した分解

julia> l == F.L && u == F.U && p == F.p
true
```
