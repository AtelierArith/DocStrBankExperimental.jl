```
kernfft = freqkernel([T::Type], kern, sz=size(kern); rfft=false)
```

`kern`の周波数空間表現を返します。これは、`kern`をサイズ`sz`の配列に埋め込み、暗黙的に周期境界条件を課す方法であり、その後フーリエ変換（周波数応答）を返します。これは時々光学伝達関数と呼ばれ、一部のフレームワークでは`psf2otf`として知られています。`rfft`が`true`の場合、実数値配列のFFT（`rfft`）が代わりに返され、最初の次元のサイズは`sz[1]`の約半分になります。

`kern`はゼロ中心である必要があります。つまり、`kern[0, 0]`はカーネルの中心を参照し、`sz`は`kern`をサポートするのに十分大きくなければなりません。[`centered`](@ref OffsetArrays.centered)を参照してください。オプションで数値型`T`を指定できます（これはFFTWがサポートする型のいずれか、`Float32`または`Float64`でなければなりません）。

`freqkernel`の逆は[`spacekernel`](@ref)です。
