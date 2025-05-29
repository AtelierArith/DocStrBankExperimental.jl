```
solve!(solver::Solver, body_aero::BodyAerodynamics, gamma_distribution=solver.sol.gamma_distribution; 
      log=false, reference_point=zeros(MVec3), moment_frac=0.1)
```

空力モデルの主解決ルーチン。参照点は凧のボディ（KB）フレーム内にあります。このバージョンは `solver.sol` 構造体を修正し、辞書を返す `solve` 関数よりも高速です。

# 引数:

  * solver::Solver: 使用するソルバー。VSMまたはLLTソルバーである可能性があります。参照: [Solver](@ref)
  * body_aero::BodyAerodynamics: 空力ボディ。参照: [BodyAerodynamics](@ref)
  * gamma_distribution: 初期循環ベクトルまたは何もない; 長さ: セグメントの数。 [m²/s]

# キーワード引数:

  * log=false: trueの場合、反復回数やその他の情報を印刷します。
  * reference_point=zeros(MVec3)
  * moment_frac=0.1: モーメント分布を計算する周りの正規化パネルのX座標。

# 戻り値

タイプ [VSMSolution](@ref) の解。
