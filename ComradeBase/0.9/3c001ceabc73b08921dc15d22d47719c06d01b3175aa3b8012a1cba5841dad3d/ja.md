```
axisdims(img::IntensityMap)
axisdims(img::IntensityMap, p::Symbol)
```

`IntensityMap`のキーを実際の内部`AbstractRectiGrid`オブジェクトとして返します。オプションで、ユーザーは`p`を使って特定の次元を要求することができます。
