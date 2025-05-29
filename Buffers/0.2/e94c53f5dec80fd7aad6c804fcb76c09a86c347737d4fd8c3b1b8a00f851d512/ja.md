```
@threadsbuffer(specs, ex)
```

指定された仕様で[`ThreadsMAllocBuffer`](@ref)オブジェクトを作成し、式`ex`を実行します。

仕様`specs`は次のようにできます：

  * `buf(100)`は、長さ`100`の`Float64`型のバッファ`buf`を作成します。
  * `buf(Int, 100)`は、長さ`100`の`Int`型のバッファ`buf`を作成します。
  * `buf(Int, 100, 4)`は、`4`スレッド用の長さ`100`の`Int`型のバッファ`buf`を作成します。
