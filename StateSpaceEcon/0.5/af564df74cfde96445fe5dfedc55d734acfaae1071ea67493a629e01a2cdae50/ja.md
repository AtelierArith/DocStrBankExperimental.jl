```
steadystatedata(model, plan; [ref=firstdate(plan) + m.maxlag))
```

与えられた `model` と `plan` に対してシミュレーション用の [`SimData`](@ref) を作成します。列はモデルの変数とショックに対応し、正しい順序で配置されます。データは定常状態で初期化されます。

定常状態の解が定常でない場合（すなわち、ゼロでない傾きの場合）、`ref` オプションを使用して定常状態レベルが与えられる期間を指定します。`ref` のデフォルトは最初のシミュレーション期間です。

[`zeroarray`](@ref) と [`zeroworkspace`](@ref) も参照してください。
