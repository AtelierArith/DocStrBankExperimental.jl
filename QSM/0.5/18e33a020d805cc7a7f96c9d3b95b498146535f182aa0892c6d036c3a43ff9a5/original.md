```
padarray!(
    xp::AbstractArray{Txp, N},
    x::AbstractArray{Tx, N},
    pad::Symbol = :fill,
    val = 0
) -> xp
```

Pad array keeping it centered at `n÷2+1`.

### Arguments

  * `xp::AbstractArray{Txp, N}`: padded array
  * `x::AbstractArray{Tx, N}`: array to pad
  * `pad::Symbol = :fill`: padding method

      * `:fill`
      * `:circular`
      * `:replicate`
      * `:symmetric`
      * `:reflect`
  * `val = 0`: pads array with `val` if `pad = :fill`

### Returns

  * `xp`: padded array
