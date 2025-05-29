```
circlepath(center::Point, radius;
    action=:none,
    reversepath=false,
    kappa = 0.5522847498307936)
circlepath(center::Point, radius, action;
    reversepath=false,
    kappa = 0.5522847498307936)
```

Bézier曲線を使用して円を作成し、現在のパスに追加します。

`circle()`を使用する代わりにこれを使用する利点の1つは、`reversepath`オプションを使用して円を反時計回りではなく時計回りに描画できることです。

魔法の値である`kappa`は`4.0 * (sqrt(2.0) - 1.0) / 3.0`です。

2つの点、バウンディングボックスの隅を返します。
