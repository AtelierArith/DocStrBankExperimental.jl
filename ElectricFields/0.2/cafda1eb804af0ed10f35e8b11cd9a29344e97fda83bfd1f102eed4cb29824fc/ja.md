```
DispersedField(f, de; spline_order=7, Bfs=20/period(F))
```

[`DispersedField`](@ref) の便利なコンストラクタで、`de` を通じて散逸された後の `f` に対して適切な時間範囲を自動的に見つけ、その結果得られたベクトルポテンシャルに [`BSpline`](@ref) をフィットさせることで、任意の時間で [`vector_potential`](@ref) と [`field_amplitude`](@ref) を評価できるようにします。ノットの数は「サンプリング周波数」`Bfs` によって影響を受けることがあります。
