```
MatterByHF{T, D, NN, BN, HFTS} <:MatterData{T, D}
```

量子系の電子構造情報のコンテナ。

≡≡≡ フィールド ≡≡≡

`Ehf::T`: 電子ハミルトニアンのハートリー–フォックエネルギー。

`nuc::NTuple{NN, String}`: 研究対象の系における原子核。

`nucCoord::NTuple{NN, NTuple{D, T}}`: 対応する原子核の座標。

`Enn::T`: 核間反発エネルギー。

`Ns::NTuple{HFTS, Int}`: 同じスピン配置の電子の数。制限付き閉殻ハートリー–フォック（RHF）では、`.Ns`の単一要素がスピンアップ電子とスピンダウン電子の両方を表します。

`occu::NTuple{HFTS, NTuple{BN, Int}}`: 標準軌道の占有数。

`occuOrbital::NTuple{HFTS, Tuple{Vararg{CanOrbital{T, D, NN}}}}`: 占有された標準軌道。

`unocOrbital::NTuple{HFTS, Tuple{Vararg{CanOrbital{T, D, NN}}}}` 占有されていない標準軌道。

`occuC::NTuple{HFTS, Matrix{T}}`: 占有された標準軌道の係数行列。

`unocC::NTuple{HFTS, Matrix{T}}`: 占有されていない標準軌道の係数行列。

`coreHsameSpin::NTuple{HFTS, Matrix{T}}`: 同じスピン配置の標準軌道のコアハミルトニアン（1体積分）。

`eeIsameSpin::NTuple{HFTS, Array{T, 4}}`: 同じスピン配置の標準軌道の電子-電子相互作用（2体積分）。

`eeIdiffSpin::Matrix{T}`: 異なるスピンを持つ標準軌道間のクーロン相互作用。

`basis::GTBasis{T, D, BN}`: ハートリー–フォック近似に使用される基底セット。

≡≡≡ 初期化メソッド ≡≡≡

```
MatterByHF(HFres::HFfinalVars{T, D, <:Any, NN, BN, HFTS}; 
           roundAtol::Real=getAtolVal(T)) where {T, D, NN, BN, HFTS} -> 
MatterByHF{T, D, NN, BN, HFTS}
```

ハートリー–フォック法の結果`HFres`から`MatterByHF`を構築します。`.occuOrbital`および`.unocOrbital`に構築された[`CanOrbital`](@ref)に格納される各パラメータは、`roundAtol`の最も近い倍数に丸められます。`roundAtol`が`NaN`に設定されている場合、丸めは行われません。
