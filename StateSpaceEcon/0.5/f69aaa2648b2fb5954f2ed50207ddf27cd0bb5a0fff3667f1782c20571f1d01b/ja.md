```
steadystateworkspace(model, plan; [ref=firstdate(plan) + m.maxlag))
```

与えられた `model` の各変数/ショックに対して [`Workspace`](@ref TimeSeriesEcon.Workspace) を作成します。これらは定常状態の解に初期化されます。

定常状態の解が定常でない場合（すなわち、ゼロでない傾き）には、`ref` オプションを使用して定常状態レベルが与えられる期間を指定します。`ref` のデフォルトは最初のシミュレーション期間です。

[`steadystatedata`](@ref) の使用をお勧めします。[`steadystatearray`](@ref) も参照してください。
