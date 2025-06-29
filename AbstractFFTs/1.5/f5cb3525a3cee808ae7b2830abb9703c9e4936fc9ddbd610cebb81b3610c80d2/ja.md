```
plan_fft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

与えられた次元（`dims`）の配列の形状と型が`A`に一致する最適化されたFFTを事前に計画します。 （最初の2つの引数は[`fft`](@ref)と同じ意味を持ちます。）FFTによって計算された線形演算子を表すオブジェクト`P`を返し、`fft(A, dims)`を迅速に計算するために必要なすべての情報を含みます。

`P`を配列`A`に適用するには、`P * A`を使用します。一般に、計画を適用するための構文は行列のそれに非常に似ています。 （計画は、計画が作成された`A`と同じサイズの配列にのみ適用できます。）事前に割り当てられた出力配列`Â`を使用して計画を適用することもでき、`mul!(Â, plan, A)`を呼び出します。 （ただし、`mul!`の場合、入力配列`A`は出力`Â`と同様に複素浮動小数点配列でなければなりません。）逆変換計画は`inv(P)`で計算でき、逆計画は`P \ Â`で適用します（逆計画はキャッシュされ、`inv`または`\`への後続の呼び出しで再利用されます）、事前に割り当てられた出力配列`A`に逆計画を適用するには`ldiv!(A, P, Â)`を使用します。

`flags`引数はFFTWプランナーのフラグのビット単位の論理和で、デフォルトは`FFTW.ESTIMATE`です。例えば、`FFTW.MEASURE`や`FFTW.PATIENT`を渡すと、異なる可能なFFTアルゴリズムをベンチマークし、最も速いものを選択するのに数秒（またはそれ以上）かかる場合があります。プランナーのフラグに関する詳細はFFTWマニュアルを参照してください。オプションの`timelimit`引数は、許可される計画時間の大まかな上限を秒単位で指定します。`FFTW.MEASURE`や`FFTW.PATIENT`を渡すと、計画作成中に入力配列`A`がゼロで上書きされる可能性があります。

[`plan_fft!`](@ref)は[`plan_fft`](@ref)と同じですが、引数に対してインプレースで動作する計画を作成します（引数は複素浮動小数点数の配列でなければなりません）。[`plan_ifft`](@ref)なども似ていますが、逆変換[`ifft`](@ref)などの同等の処理を行う計画を生成します。
