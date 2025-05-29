```
simd_shuffle_up(data::T, delta::Integer)
```

呼び出し元のSIMDレーンIDから`delta`を引いた差分のSIMDレーンIDを持つスレッドから`data`を返します。

`delta`の値は、すべてのスレッドで同じでなければなりません。この関数は、SIMDグループ内の値をラップしないため、`data`の下位`delta`レーンを変更しません。

Tは次のいずれかでなければなりません: Float32, Float16, Int32, UInt32, Int16, UInt16, Int8, または UInt8
