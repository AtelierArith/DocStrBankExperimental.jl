```
concat(dataset1::DimStack, dataset2::DimStack)::DimStack
```

2つのDimStackデータセットを連結します。キーが重複している場合、dataset1のdimarrayは上書きされます。連結された`DimStack`データセット内の`DimArray`は、元の`DimStack`データセット内のものとプログラム的に区別できません。
