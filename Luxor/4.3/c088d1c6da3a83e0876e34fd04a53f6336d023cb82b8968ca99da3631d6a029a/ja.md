```
shiftbezierhandles(bps::BezierPathSegment;
    angles=[0.1, -0.1],
    handles=[1.1, 1.1])
```

`bps`のBézierパスを制御ハンドルを移動させることで修正する新しいBezierPathSegmentを返します。`angles`の値はハンドルの角度を増加させ、`handles`の値は長さを修正します：1は長さを保持し、0.5はハンドルの長さを半分にし、2はそれを2倍にします。
