```
padarray!(
    xp::AbstractArray{Txp, N},
    x::AbstractArray{Tx, N},
    pad::Symbol = :fill,
    val = 0
) -> xp
```

配列をパディングし、`n÷2+1`で中央に保ちます。

### 引数

  * `xp::AbstractArray{Txp, N}`: パディングされた配列
  * `x::AbstractArray{Tx, N}`: パディングする配列
  * `pad::Symbol = :fill`: パディング方法

      * `:fill`
      * `:circular`
      * `:replicate`
      * `:symmetric`
      * `:reflect`
  * `val = 0`: `pad = :fill` の場合、`val` で配列をパディングします

### 戻り値

  * `xp`: パディングされた配列
