```
simd_shuffle_down(data::T, delta::Integer)
```

呼び出し元のSIMDレーンIDと`delta`の合計であるSIMDレーンIDを持つスレッドから`data`を返します。

`delta`の値は、SIMDグループ内のすべてのスレッドで同じでなければなりません。この関数は、SIMDグループの値をラップしないため、`data`の上位`delta`レーンを変更しません。

Tは次のいずれかでなければなりません: Float32, Float16, Int32, UInt32, Int16, UInt16, Int8, または UInt8
