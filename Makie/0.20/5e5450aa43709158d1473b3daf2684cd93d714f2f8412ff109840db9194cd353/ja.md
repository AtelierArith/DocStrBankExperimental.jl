```
showgradients(
    cgrads::AbstractVector{Symbol};
    h = 0.0, offset = 0.2, fontsize = 0.7,
    size = (800, length(cgrads) * 84)
)::Scene
```

与えられた色のグラデーションを水平のカラーバーとして配置します。オフセットやフォントサイズを変更した場合は、解像度を変更する必要があるかもしれません。
