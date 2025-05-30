```
deconvolution(measured, psf; <keyword arguments>)
```

`measured`と`psf`のデコンボリューションを計算します。戻り値は2つの要素を持つタプルです。最初のエントリはデコンボリューションされた画像です。2番目の戻り値はOptim.jlの最適化の出力です。

異なる損失関数、正則化子、およびマッピングのために複数のキーワード引数を指定できます。

# 引数

  * `loss=Poisson()`: measuredと同じ形状のベクトルを取る損失関数。
  * `regularizer=nothing`: `loss`と同じ形式の正則化子関数。異なる正則化子については`GR`、`TV`、`Tikhonov`およびヘルプページを参照してください。
  * `λ=0.05`: グローバル損失関数に対する正則化子の総重みを示す浮動小数点数。
  * `background=0`: 背景の強度レベルを示す浮動小数点数。
  * `mapping=Non_negative()`: 最適化の重みのマッピングを適用します。デフォルトは非負制約を達成する放物線です。
  * `iterations=nothing`: 最適化後の反復回数を指定します。確実に停止すべきです。デフォルトでは、`nothing`が提供された場合、generic_invert.jlによって20回の反復が選択されます。
  * `conv_dims`: 畳み込みが行われる次元を示すタプル。デフォルトは`conv_dims=1:ndims(psf)`です。
  * `plan_fft=true`: plan_fftが使用されるかどうかのブール値。わずかな速度向上をもたらします。
  * `padding=0`: 再構築の周りのパディング領域の量（その次元のサイズの割合）を示す浮動小数点数。FFTのラップアラウンド効果を防ぎます。`size(arr)=(400, 400)`の配列で`padding=0.05`の場合、再構築サイズは`(440, 440)`になります。ただし、パディングが>= 0.0の場合、元のサイズに切り取られた再構築のみが返されます。負のパディングの場合、絶対値が使用されますが、結果はパディングされたサイズを維持します。`padding=0`はパディングを無効にします。
  * `opt_package=Opt_Optim`: 使用される最適化のバックエンドを決定します。
  * `opt=LBFGS()`: `opt_package`に適合する選択された最適化器。
  * `opt_options=nothing`: Optim.jlによって必要とされるオプションファイルである可能性があります。反復を上書きします。
  * `initial=mean(measured)`: 初期推測の値（または配列）を定義します。これは逆マッピング関数を通じて引き出され、平均値（境界領域が使用される場合）で拡張されます。
  * `debug_f=nothing`: 現在の再構築を引数として取る必要があるデバッグ関数。

!!! note
    PSFモデルを提供したい場合は、配列の最初のエントリ（`psf[1]`）の周りに中心を合わせていることを確認してください。PSFモデルまたは測定されたPSFには`ifftshift`を使用する必要があるかもしれません。


# 例

```julia-repl
julia> using DeconvOptim, TestImages, Colors, Noise;

julia> img = Float32.(testimage("resolution_test_512"));

julia> psf = Float32.(generate_psf(size(img), 30));

julia> img_b = conv(img, psf);

julia> img_n = poisson(img_b, 300);

julia> res, o = deconvolution(img_n, psf);
```
