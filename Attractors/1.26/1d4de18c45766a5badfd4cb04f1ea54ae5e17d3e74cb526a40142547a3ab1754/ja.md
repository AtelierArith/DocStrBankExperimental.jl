```
group_features(features, group_config::GroupingConfig) → labels
```

与えられた「特徴」の反復可能なもの（通常は実数のベクトル）を設定に従ってグループ化し、ラベル（`features`と同じ長さのベクトル）を返します。可能なグループ化設定については、[`GroupingConfig`](@ref)を参照してください。
