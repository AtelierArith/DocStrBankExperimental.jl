```
gradOfHFenergy(par, basis, C, nuc, nucCoords, N=getCharge(nuc)) -> AbstractVector

gradOfHFenergy(par, bs, C, nuc, nucCoords, N=getCharge(nuc)) -> AbstractVector
```

`gradOfHFenergy`の2つのメソッド。

≡≡≡ 位置引数 ≡≡≡

`par::AbstractVector{<:ParamBox}`: 微分のためのパラメータ。

`basis::`[`GTBasis`](@ref)`{T, D} where {T, D}`: 基底セット情報。

`C::NTuple{<:Any, AbstractMatrix{T}} where T`: 選択された基底セットに対する標準軌道の係数行列。

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: 研究対象のシステム内の原子核。

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: 対応する原子核の座標。

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: 電子の総数、または同じスピン配置の電子の数。

`bs::Union{     NTuple{BN, GTBasisFuncs{T, D, 1}},      AbstractVector{<:GTBasisFuncs{T, D, 1}} } where {T, D}`: 基底関数のコレクション。

**注意:** これらの2つのメソッドのいずれかが適用される場合、ユーザーは`C`の行順序と列順序が`bs`（`basis.basis`）の要素順序と一致していることを確認する必要があります。``
