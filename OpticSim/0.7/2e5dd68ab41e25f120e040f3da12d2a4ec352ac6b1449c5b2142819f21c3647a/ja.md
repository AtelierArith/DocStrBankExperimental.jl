```
Spider(narms::Int, armwidth::T, radius::T, origin::SVector{3,T} = SVector{3,T}(0.0, 0.0, 0.0), normal::SVector{3,T} = SVector{3,T}(0.0, 0.0, 1.0)) -> Vector{Rectangle{T}}
```

`narms` 個の長方形のアームを持つ「スパイダー」遮蔽を作成します。アームは `origin` と `normal` で定義された円の周りに均等に配置されます。各アームは `armwidth`×`radius` の長方形です。

例えば、3本と4本のアームの場合、次のようになります：

```
   |         _|_
  / \         |
```
