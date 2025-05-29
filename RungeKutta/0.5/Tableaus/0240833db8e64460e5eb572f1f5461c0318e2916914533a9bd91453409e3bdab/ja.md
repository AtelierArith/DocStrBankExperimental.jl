Lobatto IIIF タブローと s ステージ

```julia
TableauLobattoIIIF(::Type{T}, s)
TableauLobattoIIIF(s) = TableauLobattoIIIF(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

参考文献:

```
Wang Fangzong and Liao Xiaobing.
A Class of Lobatto Methods of Order 2s.
Journal of Applied Mathematics, Volume 46, Pages 6-10, 2016.
```
