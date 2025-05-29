```
FusionStyle(::Sector)
FusionStyle(I::Type{<:Sector})
```

セクターの型 `I` の融合動作を記述するためのトレイトで、これは次のいずれかです。

  * `UniqueFusion()`: 2つのセクターを融合したときの単一の融合出力;
  * `SimpleFusion()`: 複数の出力があるが、各出力は最大1回しか発生しない、すなわち重複なし（例: $SU(2)$ の不変表現）;
  * `GenericFusion()`: 複数の出力があり、1回以上発生する可能性がある（例: $SU(3)$ の不変表現）。

`SimpleFusion` と `GenericFusion` の両方のサブタイプである `MultipleFusion` という抽象スーパタイプがあります。さらに、重複ラベルを必要としない融合タイプのための型エイリアス `MultiplicityFreeFusion` があり、すなわち `MultiplicityFreeFusion = Union{UniqueFusion,SimpleFusion}` です。
