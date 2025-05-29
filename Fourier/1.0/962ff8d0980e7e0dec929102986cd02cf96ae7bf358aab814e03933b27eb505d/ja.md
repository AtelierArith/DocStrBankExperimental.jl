```
imdft(ary, samples[, shift, Q])
```

2D逆DFTを行列の三重積を介して計算し、返します。shift==0の場合、これはfftshift(ifft(ifftshift(ary)))と同等であり、samples=size(ary)、Q=1です。

samplesは出力領域のサンプル数です。整数の場合、両方の次元にブロードキャストされます。それ以外の場合は、各次元を提供するためのタプルである可能性があります。

shiftは原点を移動させるために使用されます。shift=0の出力グリッドが-10:1:9 Hzをカバーしている場合、shift=10は出力グリッドを0:1:19Hzに移動させます。単位はサンプルであり、ヘルツではありません。最初の引数はx方向、つまり行列の列に沿っており、dim 0ではありません。

Qはオーバーサンプリング係数を制御します。これは、入力配列を同じ係数でゼロパディングすることと同等です。例えば、Q=2の256x256配列のmdftは、それを512x512にゼロパディングしてFFTをかけるのと同じです。

参照: [`mdft`](@ref)

# 参考文献

"Fast computation of Lyot-style coronagraph propagation" Soummer et al, oe-15-24-15935
