```
WaveletOverlap([wavelet]) <: OutcomeSpace
```

最大重複離散ウェーブレット変換 (MODWT) に基づく [`OutcomeSpace`](@ref) です。

[`probabilities`](@ref) と共に使用されると、MODWT は信号に適用され、その後、異なるウェーブレットスケールでの（正規化された）エネルギーとして確率が計算されます。これらの確率は、[Rosso2001](@citet) に従ってウェーブレットエントロピーを計算するために使用されます。明確に定義されたアウトカムスペースには、入力時系列 `x` が必要です。

デフォルトでは、ウェーブレット `Wavelets.WT.Daubechies{12}()` が使用されます。そうでない場合は、`Wavelets` パッケージからウェーブレットを選択できます（`OrthoWaveletClass` をサブタイプする必要があります）。

## アウトカムスペース

`WaveletOverlap` のアウトカムスペースは、ウェーブレットスケールを列挙する整数 `1, 2, …, N` です。これらが何を意味するのかをよりよく理解するために、[オンラインで表示](https://github.com/kahaaga/waveletentropy_example/blob/main/wavelet_entropy_example.ipynb)できるノートブックを用意しました。このように、この推定器は時系列入力にのみ機能し、明確に定義された [`outcome_space`](@ref) には入力 `x` が必要です。
