```
ConnectedRegion(outer, inner)
```

境界成分を指定することによって開いた連結領域を構築します。`outer` 境界は `nothing` または閉じた曲線またはパスである可能性があります。`inner` 境界は、1つ以上の交差しない閉じた曲線またはパスのベクトルである必要があります。定義された領域は、外部境界の内部にあり、与えられた曲線の向きに関係なく、内側の境界のすべての成分の外部にあります。
