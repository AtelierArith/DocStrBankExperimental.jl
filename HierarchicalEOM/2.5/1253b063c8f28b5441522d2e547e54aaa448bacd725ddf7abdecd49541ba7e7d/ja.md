```
Propagator(M, Δt; threshold, nonzero_tol)
```

`FastExpm.jl`を使用して、特定の時間ステップ$\Delta t$を持つ与えられたHEOMリウビリアンスーパーオペレーター行列$M$から伝播子行列を計算します。すなわち、$\exp(M * \Delta t)$です。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `Δt::Real` : 特定の時間ステップ（時間間隔）。
  * `threshold::Real` : テイラー級数の閾値を決定します。デフォルトは`1.0e-6`です。
  * `nonzero_tol::Real` : 各計算ステップで`nonzero_tol`より小さい要素を削除してスパース性を保持します。デフォルトは`1.0e-14`です。

詳細については、[`FastExpm.jl`](https://github.com/fmentink/FastExpm.jl)を参照してください。

# 戻り値

  * `::SparseMatrixCSC{ComplexF64, Int64}` : 伝播子行列
