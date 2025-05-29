```
ParaboloidSurface(apex, radius, focallength)
```

R³に埋め込まれ、焦点軸から`radius`の距離まで延びる放物面で、焦点軸はz方向に沿っており、`apex`（放物面の頂点）を通ります。放物面の方程式は次のとおりです：

$$
f(x, y) = \frac{(x - x_0)^2 + (y - y_0)^2}{4f} + z_0\qquad\text{for } x^2 + y^2 < r^2,
$$

ここで、$(x_0, y_0, z_0)$は放物線の頂点、$f$は焦点距離、$r$はクリップ半径です。

```
ParaboloidSurface(apex, radius)
```

これは焦点距離が1の放物面を作成します。

```
ParaboloidSurface(apex)
```

これは焦点距離が1で、単位半径のリムを持つ放物面を作成します。

```
ParaboloidSurface()
```

上記と同じですが、ここでは頂点が`Apex(0, 0, 0)`にあります。

詳細は[https://en.wikipedia.org/wiki/Paraboloid](https://en.wikipedia.org/wiki/Paraboloid)を参照してください。
