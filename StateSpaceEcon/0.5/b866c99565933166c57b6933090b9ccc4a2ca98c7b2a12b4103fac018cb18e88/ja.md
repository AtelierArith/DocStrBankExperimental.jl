```
steadystatearray(model, plan; [ref=firstdate(plan) + m.maxlag])
```

与えられたモデルとプランに対して、適切な次元の `Matrix{Float64}` を作成します。これは定常状態に初期化されます。

定常状態の解が定常でない場合（すなわち、ゼロでない傾きの場合）、`ref` オプションを使用して定常状態レベルが与えられる期間を指定します。`ref` のデフォルトは最初のシミュレーション期間です。

この関数は `Matrix` を返します。 [`zerodata`](@ref) を使用することをお勧めします。これは [`SimData`](@ref) を返します。 [`zeroworkspace`](@ref) も参照してください。

!!! note "非推奨の注意"
    `zeroarray(model, range)` は将来のバージョンで削除されます。シミュレーション `Plan` を常に明示的に作成してください。

