```
DensityOfStates(M, ρ, d_op, ωlist; solver, verbose, filename, SOLVEROptions...)
```

周波数領域におけるフェルミオン系の状態密度を計算します。

$$
    \pi A(\omega)=\textrm{Re}\left\{\int_0^\infty dt \left[\langle d(t) d^\dagger(0)\rangle^* + \langle d^\dagger(t) d(0)\rangle \right] e^{-i\omega t}\right\},
$$

# パラメータ

  * `M::AbstractHEOMLSMatrix` : `ODD`-パリティ演算子に作用するHEOMLS行列。
  * `ρ::Union{QuantumObject,ADOs}` : 系の密度行列または補助密度演算子。
  * `d_op::QuantumObject` : フェルミオン系に作用する消滅演算子（上記の$d$）。
  * `ωlist::AbstractVector` : 解く特定の周波数点。
  * `solver::SciMLLinearSolveAlgorithm` : パッケージ`LinearSolve.jl`のソルバー。デフォルトは`KrylovJL_BICGSTAB(rtol=1e-12, atol=1e-14)`。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは`true`。
  * `filename::String` : ファイル名が指定された場合、各ωのスペクトルの値が解決プロセス中にファイル"filename.txt"に保存されます。
  * `SOLVEROptions` : ソルバーのための追加オプション

# 注意事項

  * `solver`および`SOLVEROptions`に関する詳細については、[`LinearSolve.jl`](http://linearsolve.sciml.ai/stable/)を参照してください。

# 戻り値

  * `dos::AbstractVector` : 指定された`ωlist`に対応する状態密度のリスト

```
