```
u_to=interpolate(grid_to, u_from, grid_from;eps=1.0e-14,trybrute=true)
```

グリッド `grid_from` 上の関数 `u_from` の区分線形補間をグリッド `grid_to` に対して行います。第二次元がグリッドノードに対応する行列やベクトルに対して機能します。

!!! warning
    凸でない領域では遅くなる可能性があります。`trybrute==false` の場合、失敗することさえあります。


!!! warning
    現在、単体グリッドのみに実装されています。

