```
evaluate(::NormalizedCosineDistance, a, b)
```

2つのベクトル間のコサイン距離を計算します。正規化されたベクトルを期待します。メトリック関数を期待する場合は、NormalizedAngleDistanceを使用してください（三角不等式が必要ない場合は、cosine_distanceがより高速な代替手段です）。
