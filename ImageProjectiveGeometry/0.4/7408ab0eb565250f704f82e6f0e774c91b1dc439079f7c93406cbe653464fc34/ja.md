makeinhomogeneous - 同次座標を非同次座標に変換します

```
Usage:  x = makehomogeneous(hx)

Argument:
        hx  - 同次座標の N x npts 配列。

Returns:
        x - 非同次座標の (N-1) x npts 配列
```

Warning:  無限大の点がある場合（スケール = 0）、これらの点の座標は単にスケール座標を引いたものが返されます。

See also: makehomogeneous(), hnormalise()
