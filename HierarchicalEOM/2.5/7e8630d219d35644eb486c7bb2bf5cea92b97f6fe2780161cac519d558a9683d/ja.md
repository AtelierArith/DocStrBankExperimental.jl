```
PowerSpectrum(M, ρ, P_op, Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)
```

周波数領域でのシステムのパワースペクトルを計算します。

$$
\pi S(\omega)=\textrm{Re}\left\{\int_0^\infty dt \langle P(t) Q(0)\rangle e^{-i\omega t}\right\},
$$

# 入力演算子 `Q_op` が `EVEN` 対称性を持つ場合のスペクトル計算:

次のパラメータを設定することを忘れないでください:

  * `M::AbstractHEOMLSMatrix`: `EVEN` 対称性である必要があります。

# 入力演算子 `Q_op` が `ODD` 対称性を持つ場合のスペクトル計算:

次のパラメータを設定することを忘れないでください:

  * `M::AbstractHEOMLSMatrix`: `ODD` 対称性である必要があります。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMLS行列。
  * `ρ::Union{QuantumObject,ADOs}` : システムの密度行列または補助密度演算子。
  * `P_op::Union{QuantumObject,HEOMSuperOp}`: システムに作用するシステム演算子（または `HEOMSuperOp`）$P$。
  * `Q_op::Union{QuantumObject,HEOMSuperOp}`: システムに作用するシステム演算子（または `HEOMSuperOp`）$Q$。
  * `ωlist::AbstractVector` : 解く特定の周波数点。
  * `reverse::Bool` : `true` の場合、$\langle P(-t)Q(0) \rangle = \langle P(0)Q(t) \rangle = \langle P(t)Q(0) \rangle^*$ を計算します。デフォルトは `false` です。
  * `solver::SciMLLinearSolveAlgorithm` : パッケージ `LinearSolve.jl` のソルバー。デフォルトは `KrylovJL_BICGSTAB(rtol=1e-12, atol=1e-14)` です。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは `true` です。
  * `filename::String` : ファイル名が指定された場合、解決プロセス中に各 ω のスペクトル値が "filename.txt" に保存されます。
  * `SOLVEROptions` : ソルバーのための追加オプション。

# 注意事項

  * `solver` と `SOLVEROptions` の詳細については、[`LinearSolve.jl`](http://linearsolve.sciml.ai/stable/) を参照してください。

# 戻り値

  * `spec::AbstractVector` : 指定された `ωlist` に対応するスペクトルリスト。

```
