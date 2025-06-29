```
kp, ki, fig = stabregionPID(P, [ω]; kd=0, doplot=false, form=:standard)
```

このプログラムによって生成された曲線のセグメントは、伝達関数 P(s) を持つプロセスの安定性領域の境界です。提供された微分ゲインは並列形式、すなわち kp + ki/s + kd s の形式で期待されますが、結果は `form` キーワードによって与えられる任意の形式に変換できます。曲線は次のように分析することによって見つかります。

$$
P(s)C(s) = -1 ⟹ \\
|PC| = |P| |C| = 1 \\
arg(P) + arg(C) = -π
$$

`P` が関数（例: s -> exp(-sqrt(s))）である場合、PIコントローラを使用したフィードバックループの安定性は、任意の解析関数を持つモデルのプロセスに対して分析できます。詳細は [`loopshapingPI`](@ref)、[`loopshapingPID`](@ref)、[`pidplots`](@ref) を参照してください。
