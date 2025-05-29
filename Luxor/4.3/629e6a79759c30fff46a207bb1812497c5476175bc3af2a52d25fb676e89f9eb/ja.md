```
easeinoutbezier(t, b, c, d, cpt1, cpt2)
```

このイージング関数は、通常の`t`、`b`、`c`、`d`に加えて、2つのポイントを取ります。これらは、`Point(0, 0)`から`Point(1.0, 1.0)`の間に描かれたベジェ曲線の正規化された制御点です。ベジェの`y`値は`t`のためのイージングされた値です。

あなたの`frame()`生成関数の中で、シーンが`easeinoutbezier`イージング関数を指定している場合、次のように使用できます：

```julia
...
lineareasing = rescale(framenumber, 1, scene.framerange.stop)
beziereasing = scene.easingfunction(lineareasing, 0, 1, 1,
    Point(0.25, 0.25), Point(0.75, 0.75))
...
```

これらの2つの制御点は`0/0`と`1/1`の間の線上にあるため、線形イージング（`lineartween()`または`easingflat`）と同等です。

しかし、次の例では、2つの制御点が方向を変える前に戻る波のような曲線を定義します。このイージング関数を使用してアニメーションを行うと、オブジェクトはしばらく「逆行」します。

```julia
lineareasing = rescale(framenumber, 1, scene.framerange.stop)
beziereasing = scene.easingfunction(lineareasing, 0, 1, 1,
    Point(0.01, 1.99), Point(0.99, -1.5))
```
