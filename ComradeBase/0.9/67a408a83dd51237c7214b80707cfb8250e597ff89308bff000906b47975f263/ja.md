```
intensitymap!(img::AbstractIntensityMap, mode;, executor = SequentialEx())
```

`model`の強度マップまたは*画像*を計算します。これにより、`IntensityMap`オブジェクト`img`が更新されます。

オプションで、ユーザーはループの実行方法を指定するために`FLoops.jl`を使用する`executor`を指定できます。デフォルトでは、単一コアを使用して画像を構築する`SequentialEx`を使用します。
