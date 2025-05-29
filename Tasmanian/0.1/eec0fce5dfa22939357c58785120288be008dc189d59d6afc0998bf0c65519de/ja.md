```
getLoadedPoints(tsg::TasmanianSG)
```

は、既存の補間にロードされたポイントを返します。

出力: サイズ getNumDimensions() X getNumNeeded() の行列     各列は1つのポイントに対応します     getNumLoaded() == 0 の場合、zeros(2) を返します
