```
PseudoTransient(;
    concrete_jac = nothing, linesearch = missing, alpha_initial = 1e-3,
    linsolve = nothing,
    autodiff = nothing, jvp_autodiff = nothing, vjp_autodiff = nothing
)
```

擬似過渡法 [coffey2003pseudotransient](@cite) の実装で、加速された方法で定常状態の問題を解決するために使用されます。これは、非線形問題の初期値を統合するために適応的な時間ステッピングを使用し、所望の定常状態で十分な精度が達成されるまで進め、ニュートン法に切り替えて迅速な収束を得ることができます。この実装は特に「切り替え進化緩和」 [kelley1998convergence](@cite) SER メソッドを使用しています。

### キーワード引数

  * `alpha_initial` : 初期擬似時間ステップ。デフォルトは `1e-3` です。これが小さいと、収束するためにより多くの反復が必要になりますが、より安定する可能性があります。
