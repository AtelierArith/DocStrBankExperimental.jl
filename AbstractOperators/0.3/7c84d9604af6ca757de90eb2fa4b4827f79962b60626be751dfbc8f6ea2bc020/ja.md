`Compose(A::AbstractOperator,B::AbstractOperator)`

ショートハンドコンストラクタ: 

`A*B` 

異なる `AbstractOperator` を合成します。演算子 `A` と `B` の定義域と値域が一致する必要があります。すなわち、`size(A,2) == size(B,1)` かつ `domainType(A) == codomainType(B)` です。

```julia
julia> Compose(DFT(16,2),Variation((4,4)))
ℱc*Ʋ  ℝ^(4, 4) -> ℝ^(16, 2)

julia> MatrixOp(randn(20,10))*DCT(10)
▒*ℱc  ℝ^10 -> ℝ^20

```
