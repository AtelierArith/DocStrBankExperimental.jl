```
eccentricities(g, distmx=weights(g))
eccentricities(g, vs, distmx=weights(g))
```

は `[eccentricity(g,v,distmx) for v in vs]` を返します。`vs` が指定されていない場合、グラフ内のすべてのノードを考慮します。

関連情報として [`eccentricity`](@ref) を参照してください。

注意: `eccentricity` によって返されるエccentricity ベクトルは、いくつかのエccentricity 関連の測定値（[`periphery`](@ref)、[`center`](@ref)）の入力として最終的に使用される可能性があります。
