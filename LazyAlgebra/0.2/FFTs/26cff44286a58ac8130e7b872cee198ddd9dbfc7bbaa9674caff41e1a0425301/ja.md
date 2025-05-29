# 循環畳み込み演算子

循環畳み込み演算子 `H` は次のように定義されます：

```julia
H  = (1/n)*F'*Diag(mtf)*F
```

ここで `n` は要素の数、`F` は離散フーリエ変換演算子、`mtf` は変調伝達関数です。

演算子 `H` は次のように作成できます：

```julia
H = CirculantConvolution(psf; flags=FFTW.MEASURE, timelimit=Inf, shift=false)
```

ここで `psf` は点拡散関数（PSF）です。PSF は離散フーリエ変換の規約に従って中心に配置されていると仮定されます。PSF が幾何学的に中心にある場合は、`ifftshift` またはキーワード `shift` を使用できます：

```julia
H = CirculantConvolution(ifftshift(psf))
H = CirculantConvolution(psf, shift=true)
```

指定できるキーワードは次のとおりです：

  * `shift`（デフォルトは `false`）は、`psf` に `ifftshift` を適用するかどうかを示します。
  * `normalize`（デフォルトは `false`）は、`psf` をその値の合計で割るかどうかを示します。このキーワードは実数値の PSF のみで利用可能です。
  * `flags` は FFTW プランナーのフラグのビット単位の論理和で、デフォルトは `FFTW.MEASURE` です。演算子を何度も使用する場合（反復法など）、少なくとも `flags=FFTW.MEASURE`（デフォルト）を使用することをお勧めします。これは一般的に `flags=FFTW.ESTIMATE` と比較してより高速な変換を提供します。
  * `timelimit` は、許可される計画時間の大まかな上限を秒単位で指定します。

演算子は通常の線形演算子として使用できます：`H(x)` または `H*x` で `x` と `H` の畳み込みを計算し、`H'(x)` または `H'*x` で `H` の随伴を `x` に適用します。

パフォーマンスをわずかに改善するために、操作の結果を格納する配列 `y` を提供できます：

```julia
apply!(y, [P=Direct,] H, x) -> y
apply!(y, H, x)
apply!(y, H', x)
```

提供された場合、`y` は `x` とは異なるメモリ位置に存在する必要があります。
