```
kern = spacekernel(kernfft, axs; rfftsz=0)
```

`kernfft`の実空間表現を返します。これはカーネルの周波数空間表現です。逆フーリエ変換を実行し、暗黙的に周期境界条件を課し、出力の軸を`axs`にトリムおよび切り詰めます。デフォルトでは、`kernfft`は`fft`によって生成されたと仮定されます。もし`rfft`によって生成された場合は、最初の次元の元のサイズを指定してください。（`kernfft`が[`freqkernel`](@ref)によって生成された場合、これは単に`sz[1]`です。）

`spacekernel`の逆は[`freqkernel`](@ref)です。
