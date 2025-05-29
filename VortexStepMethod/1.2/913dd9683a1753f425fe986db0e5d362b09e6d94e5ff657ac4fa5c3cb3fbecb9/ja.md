```
solve(solver::Solver, body_aero::BodyAerodynamics, gamma_distribution=nothing; 
      log=false, reference_point=zeros(MVec3))
```

空力モデルの主解決ルーチン。基準点は凧の本体 (KB) フレームにあります。参照: [solve!](@ref)

# 引数:

  * solver::Solver: 使用するソルバーで、VSMまたはLLTソルバーのいずれかです。参照: [Solver](@ref)
  * body_aero::BodyAerodynamics: 空力的な本体。参照: [BodyAerodynamics](@ref)
  * gamma_distribution: 初期循環ベクトルまたは何もない; 長さ: セグメントの数。 [m²/s]

# キーワード引数:

  * log=false: trueの場合、反復回数やその他の情報を印刷します。
  * reference_point=zeros(MVec3)

# 戻り値

結果を含む辞書。
