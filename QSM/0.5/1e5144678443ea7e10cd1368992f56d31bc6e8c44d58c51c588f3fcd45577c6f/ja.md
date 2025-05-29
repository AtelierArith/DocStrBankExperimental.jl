```
psf2otf(
    psf::AbstractArray{<:Number, N},
    sz::NTuple{N, Integer} = size(psf);
    rfft::Bool = false,
) -> otf
```

MATLABの`psf2otf`関数の実装。

### 引数

  * `psf::AbstractArray{T<:Number, N}`: 点拡散関数
  * `sz::NTuple{N, Integer}`: 出力配列のサイズ; `psf`より小さくてはいけません

### キーワード

  * `rfft::Bool = false`:

      * `T<:Real`: `fft`を計算する（`false`）または`rfft`を計算する（`true`）
      * `T<:Complex`: 使用されていません

### 戻り値

  * `otf`: 光学伝達関数
