```
longitude_circshift(X::ClimArray [, l]; wrap = true) → Y::ClimArray
```

`Base.circshift`と同じ動作を行いますが、`X`の経度次元に対してのみ、シフト`l`を適用します。`wrap = true`の場合、経度はモジュロ演算を使用して(-180, 180)度にラップされます。

`l`が指定されていない場合、すべての経度が> 180になるように必要なだけシフトされます（`wrap`が有効な場合はラップも行われます）。

`X`に`CoordinateSpace`がある場合、経度-緯度は1次元であるため、シフトは行われませんが、経度は依然としてシフトされます。
