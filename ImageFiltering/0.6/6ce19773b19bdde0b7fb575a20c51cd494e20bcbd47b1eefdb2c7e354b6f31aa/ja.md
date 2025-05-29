```
imfilter!(::AbstractResource{FFT}, imgfilt, img, kernel, NoPad())
```

配列 `img` をカーネル `kernel` でフィルタリングし、その相関を計算して結果を `imgfilt` に格納します。これは高速フーリエ変換 (FFT) アルゴリズムを使用します。必要なパディングはすでに `img` に適用されている必要があります。パディングを適用したい場合は、代わりに次のように呼び出します。

```
imfilter!(::AbstractResource{FFT}, imgfilt, img, kernel, border)
```

特定の `border` を指定するか、または次のようにしてデフォルトのパディングを使用します。

```
imfilter!(imgfilt, img, kernel, Algorithm.FFT())
```

関連情報: [`imfilter`](@ref).
