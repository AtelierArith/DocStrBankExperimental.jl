```
ConstrainedSystems.init(u0,tspan,sys::ILMSystem,[alg=LiskaIFHERK()/HETrapezoidalAB2()])
```

時間変化する浸透層システムのPDEを記述した`sys`のために、積分器を初期化します。キーワードアルゴリズムのデフォルトの時間進行アルゴリズムは、システムに可逆な`bc_regulator`演算子があるかどうかに基づいて自動的に選択されます。もしそうであれば、`HETrapezoidalAB2()`が選択されます。そうでなければ、`LiskaIFHERK()`が選択されます。どちらも二次精度です。もう一つの選択肢は`IFHEEuler()`で、可逆な`bc_regulator`行列がない問題にも適しています。
