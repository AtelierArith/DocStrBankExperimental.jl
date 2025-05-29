ビジュアライザーで矢印を描画するためのヘルパータイプ。

使用法：

`vis`という名前の`Visualizer`がある場合、次のように矢印を作成できます。

```
ArrowVisualizer arrow(vis)
setobject!(arrow)
```

次に、次のように矢印の基点と方向を設定できます。

```
settransform!(arrow, Point(0.0, 0.0, 0.0), Vec(0.5, 0.5, 0.0))
```

この`settransform!`は、アニメーションを開始する前に`setobject!`を行う限り、`Animation`内で正しく動作することに注意してください。
