```
GroupViaNearestFeature(templates; kwargs...)
```

[`AttractorsViaFeaturizing`](@ref)で特徴をグループ化する方法に関する指示を含む構造体を初期化します。`GroupViaNearestFeature`は、特徴のベクトルである`template`を受け取ります。次に、[`AttractorsViaFeaturizing`](@ref)の初期条件から生成された特徴は、`templates`内で最も近い特徴に基づいてラベル付けされます（ラベルは最も近いテンプレートのインデックスです）。

`templates`は、キーをテンプレートにマッピングするベクトルまたは辞書である可能性があります。内部的には、すべてのテンプレートはパフォーマンスのために`SVector`に変換されます。したがって、`templates`と[`AttractorsViaFeaturizing`](@ref)の`featurizer`関数の出力の両方が`SVector`型を返すことを強く推奨します。

## キーワード引数

  * `metric = Euclidean()`: 特徴空間における距離を定量化するために使用されるメトリック。
  * `max_distance = Inf`: 特徴とその最も近いテンプレートとの間で割り当てられるために許可される最大距離。デフォルトでは、`Inf`は距離に関係なく特徴が最も近いテンプレートに割り当てられることを保証します。最も近いテンプレートに対して`max_distance`を超える特徴は`-1`とラベル付けされます。
