```
padfastfft(
    x::AbstractArray{T, N},
    ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N));
    pad::Symbol = :fill,
    val = zero(T),
    rfft::Bool = false,
) -> typeof(similar(x, szp))
```

配列 `x` を、サイズ `ksz` のカーネルとの畳み込みのために高速 fft サイズにパディングし、配列を `n÷2+1` で中心に保ちます。

### 引数

  * `x::AbstractArray{T, N}`: パディングする配列
  * `ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N))`: 畳み込みカーネルのサイズ

      * `ksz[n] < 0`: 次元 n のパディングなし

### キーワード

  * `pad::Symbol = :fill`: パディング方法

      * `:fill`
      * `:circular`
      * `:replicate`
      * `:symmetric`
      * `:reflect`
  * `val = 0`: `pad = :fill` の場合、配列を `val` でパディング
  * `rfft::Bool = false`: 最初の次元を偶数に強制 (`true`)

### 戻り値

  * `typeof(similar(x, szp))`: パディングされた配列
