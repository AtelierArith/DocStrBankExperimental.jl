```
GridHex(startpoint, radius, width=1200.0, height=1200.0)
```

六角形グリッドを定義し、`startpoint`から始めてx軸に沿って進み、その後y軸に沿って進みます。`radius`は各六角形を囲む円の半径です。連続する六角形の中心間のx方向の距離は次のようになります：

$$
\frac{\sqrt{(3)} \text{radius}}{2}
$$

グリッドから次の点を取得するには、`nextgridpoint(g::Grid)`を使用します。

グリッドポイントがなくなると、ラップして再び始まります。
