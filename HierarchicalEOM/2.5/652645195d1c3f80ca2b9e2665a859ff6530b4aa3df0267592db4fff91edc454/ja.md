```
HEOMsolve(M, ρ0, Δt, steps; e_ops, threshold, nonzero_tol, verbose, filename)
heomsolve(M, ρ0, Δt, steps; e_ops, threshold, nonzero_tol, verbose, filename)
```

補助密度演算子の時間発展を、`FastExpm.jl`によって生成された伝播子に基づいて解きます。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `ρ0::Union{QuantumObject,ADOs}` : システムの初期状態（密度行列）または初期補助密度演算子（`ADOs`）
  * `Δt::Real` : 特定の時間ステップ（時間間隔）。
  * `steps::Int` : 時間ステップの数
  * `e_ops::Union{Nothing,AbstractVector}`: 期待値を計算するための演算子のリスト。
  * `threshold::Real` : テイラー級数の閾値を決定します。デフォルトは`1.0e-6`です。
  * `nonzero_tol::Real` : 各計算ステップで`nonzero_tol`未満の要素を削除してスパース性を保持します。デフォルトは`1.0e-14`です。
  * `verbose::Bool` : プロセス中に詳細な出力と進捗バーを表示するかどうか。デフォルトは`true`です。
  * `filename::String` : ファイル名が指定された場合、解決プロセス後に各時間点でのADOがJLD2ファイル「filename.jld2」に保存されます。

# 注意事項

  * [`ADOs`](@ref)はキーワード引数`e_ops`に依存して保存されます。
  * `e_ops`が指定されている場合、解は最終的な`ADOs`のみを保存します。そうでない場合、`tlist = 0:Δt:(Δt * steps)`に対応するすべての`ADOs`が保存されます。
  * 伝播子の詳細については、[`FastExpm.jl`](https://github.com/fmentink/FastExpm.jl)を参照してください。

# 戻り値

  * `sol::TimeEvolutionHEOMSol` : 階層的EOMの解。詳細は[`TimeEvolutionHEOMSol`](@ref)を参照してください。

!!! note
    `heomsolve`は`HEOMsolve`の同義語です。

