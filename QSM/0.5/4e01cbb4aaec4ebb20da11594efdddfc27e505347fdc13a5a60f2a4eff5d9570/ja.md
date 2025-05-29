```
fastfftsize(
    sz::NTuple{N, Integer},
    ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N));
    rfft::Bool = false
) -> NTuple{N, Integer}
```

次の高速FFTサイズは、畳み込みのために`sz`以上で、サイズ`ksz`のカーネルと共に使用されます。

### 引数

  * `x::AbstractArray{T, N}`: パディングする配列
  * `ksz::NTuple{M, Integer} = ntuple(_ -> 0, Val(N))`: 畳み込みカーネルサイズ

      * `ksz[n] < 0`: 次元nのパディングなし

### キーワード

  * `rfft::Bool = false`: 最初の次元を偶数に強制する（`true`）

### 戻り値

  * `NTuple{N, Integer}`: 高速FFTサイズ
