```
struct SPMF_NEP{T<:AbstractMatrix,Ftype}  <: AbstractSPMF{T}
function SPMF_NEP(AA, fii [,check_consistency=true] [,Schur_fact = false]
                  [,align_sparsity_patterns = false] [,Ftype=ComplexF64])
```

`SPMF_NEP`は、*行列*と*関数*の*積の和*によって定義される`NEP`です。すなわち、

$$
M(λ)=∑_i A_i f_i(λ).
$$

すべての行列$A_0,...$はサイズ$n×n$であり、$f_i$は関数です。関数$f_i$は、標準的な行列関数の意味で行列に対して定義されている必要があります。コンストラクタは、行列`AA`と関数`fii`からなる`SPMF_NEP`を作成します。

# パラメータ

  * `AA`は行列の`Vector`です。行列は同じ型である必要があります。異なる型のNEPが必要な場合は、[`SumNEP`](@ref)を使用して2つの`SPMF_NEP`の和を構築できます。
  * `fii`は関数の`Vector`です。各関数は1つのパラメータ`S`を取ります。関数はスカラー有効関数および行列関数の両方として利用可能でなければなりません。`S`が正方行列の場合、`fii[k](S)`も正方行列でなければなりません。`S`がスカラーの場合、`fii[k](S)`はスカラーです。
  * `check_consistency`（デフォルトは`true`）は、`fii`がすべての関数が行列とスカラーの両方に対して有効であるという条件を満たしていることを確認するためにテストを実行するかどうかを決定します。これは`@code_typed`を使用して行われ、関数はその意味で型安定である必要があります。
  * `align_sparsity_patterns`（デフォルトは`false`）は、スパース行列（`SparseMatrixCSC`）にのみ影響します。`align_sparsity_patterns=true`の場合、`SparseMatrixCSC`行列は`colptr`と`rowval`が同一の同等の`SparseMatrixCSC`行列に置き換えられます。これにより、`compute_Mder`などのいくつかの関数の速度が向上します。`align_sparsity_patterns=true`の場合、NEP内の行列は読み取り専用と見なされるべきです。スパースパターンが完全にまたはほとんど異なる場合、このフラグをfalseに設定する方が効率的かもしれません。
  * `Ftype`（デフォルトは`ComplexF64`）は、関数の基礎となる型を決定します。任意の関数の出力は、入力と`Ftype`の昇格型よりも「小さい」必要があります。より正確には、`F=fii[k]`の場合、型の論理は次のようになります`eltype(F(λ))=promote_type(eltype(λ),Ftype)`。
  * `Schur_fact`（デフォルトは`false`）は、`compute_MM`関数が計算を行う前に行列を三角化するかどうかを決定します。これは、大きな行列に対してはより高速になる可能性があります。

# 例

```julia-repl
julia> A0=[1 3; 4 5]; A1=[3 4; 5 6];
julia> id_op=S -> one(S) # 注意: 行列とスカラーの両方に対して有効であるためにone(S)を使用します
julia> exp_op=S -> exp(S)
julia> nep=SPMF_NEP([A0,A1],[id_op,exp_op]);
julia> compute_Mder(nep,1)-(A0+A1*exp(1))
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
```
