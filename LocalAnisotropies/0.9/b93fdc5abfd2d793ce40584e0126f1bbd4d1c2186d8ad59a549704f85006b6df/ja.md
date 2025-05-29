```
reference_magnitude(localaniso, axis)
reference_magnitude!(localaniso, axis)
```

`localaniso`の大きさを、`axis`を単位参照として設定することで再スケールします。`axis`は:X, :Yまたは:Zのいずれかです。

## 例

例えば、大きさが[1.0, 0.2]の点を考えます。これを範囲=10mのExponentialVariogramでスケーリングすると、この点でのXの範囲は10m、Yの範囲は2mになります。最初に`reference_magnitude!(localaniso, :Y)`を呼び出すと、大きさは[5.0, 1.0]に変わり、同じ以前の変動にスケーリングすると、Xの範囲は50m、Yの範囲は10mになります。
