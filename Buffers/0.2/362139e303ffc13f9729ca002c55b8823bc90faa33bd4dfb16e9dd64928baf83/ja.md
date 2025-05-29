```
@buffer(specs, ex)
```

指定された仕様 `specs` を持つ [`MAllocBuffer`](@ref) オブジェクトを作成し、バッファを使って式 `ex` を実行します。

`specs` は以下の形式を持ちます：

  * `buf(100)` は、長さ `100` の `Float64` 型のバッファ `buf` を作成します。
  * `buf(Int, 100)` は、長さ `100` の `Int` 型のバッファ `buf` を作成します。

式が実行された後、バッファは解放されます。

# 例

```julia
@buffer buf(Float64, 300) begin
  A = alloc!(buf, 10, 10)
  B = alloc!(buf, 10, 10)
  C = alloc!(buf, 10, 10)
  rand!(A)
  rand!(B)
  @tensor C[i,j] = A[i,l] * B[l,j]
end
```
