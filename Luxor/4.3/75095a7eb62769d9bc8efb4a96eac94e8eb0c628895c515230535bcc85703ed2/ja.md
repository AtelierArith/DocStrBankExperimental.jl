```
box(pt::Point, width, height; action=:none, vertices=false)
box(pt::Point, width, height, action=:none; vertices=false)
```

点 `pt` を中心に幅と高さを持つボックス/長方形を作成します。`vertices=true` を使用すると、アクションを適用するのではなく、4つの隅の点の配列を返します。

`reversepath` はパスの方向を逆にします。
