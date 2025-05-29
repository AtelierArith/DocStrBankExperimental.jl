```
    CDRect
```

`CosArray`による左下および右上点形式の長方形の表現

*注意*: `CDRect`は`Rectangle`パッケージの`Rect`オブジェクトにマッピングされます。

# 例

```
julia> CDRect(CosArray(CosObject[CosInt(0), CosInt(0), CosInt(840), CosFloat(640)]))
Rect:[0.0 0.0 840.0 640.0]
```
