```
NLevelWaveguideOperator{B1,B2} <: NWaveguideOperator{BL,BR}
```

Nレベル遷移と波導演算子を同時に高速に処理するための構造。この演算子は、Nレベルシステム内のレベル間の遷移演算子と波導演算子を組み合わせたものです。

# フィールド

  * `basis_l::B1`: 左基底
  * `basis_r::B2`: 右基底
  * `factor::ComplexF64`: 複素数の前因子
  * `op::AbstractOperator`: 波導演算子
  * `loc`: 演算子の位置インデックス
  * `n_to::Int`: 遷移のターゲットレベル
  * `n_from::Int`: 遷移のソースレベル
  * `indexing::WaveguideIndexing`: 効率的な状態ベクトルの乗算のためのインデクシング構造

# 例

```julia
# Nレベルシステム内のレベル2と1の間に遷移を作成し、波導演算子と組み合わせる
op = NLevelWaveguideOperator(basis_l, basis_r, 1.0, waveguide_op, [1,2], 2, 1)
```
