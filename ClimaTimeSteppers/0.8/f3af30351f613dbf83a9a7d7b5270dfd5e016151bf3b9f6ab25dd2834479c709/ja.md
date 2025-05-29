```
EisenstatWalkerForcing(;
    initial_rtol = 0.5,
    γ = 1,
    α = 2,
    min_rtol_threshold = 0.1,
    max_rtol = 0.9,
)
```

論文「Choosing the Forcing Terms in an Inexact Newton Method」におけるS.C. EisenstatとH.F. Walkerによる「Choice 2」と呼ばれる`ForcingTerm`。`initial_rtol`、`min_rtol_threshold`、および`max_rtol`の値はすべて`[0, 1)`の範囲内でなければならず、`γ`の値は`[0, 1]`の範囲内で、`α`の値は`(1, 2]`の範囲内でなければなりません。これらの値はすべて、Newton-Krylov法が過剰解決するのを防ぐために調整できます。もし`x`と`f!`が特定の仮定を満たすなら、この強制項はNewton-Krylov法が`α`の順序で収束することを保証します。より大きな`α`の値はより高い収束順序を保証しますが、過剰解決の確率も高くなることに注意してください。

この強制項は「Choice 1」と呼ばれるものの代わりに実装されました。なぜなら、実装が大幅に簡単で、`rtol[n]`を計算するために`‖f(x[n])‖`の値だけが必要だからです。一方、「Choice 1」ではKrylovソルバーからの最終残差のノルムも必要です。
