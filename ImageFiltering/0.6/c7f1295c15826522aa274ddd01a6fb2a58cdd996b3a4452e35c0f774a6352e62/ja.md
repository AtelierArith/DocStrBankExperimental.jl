```
imfilter!(::AbstractResource, imgfilt, img, kernel, NoPad(), [inds=axes(imgfilt)])
```

配列 `img` をカーネル `kernel` でフィルタリングし、その相関を計算して結果を `imgfilt` に格納します。デフォルトでは有限インパルス応答 (FIR) アルゴリズムが使用されます。必要なパディングはすでに `img` に供給されている必要があります。パディングを適用したい場合は、代わりに次のように呼び出します。

```
imfilter!([r::AbstractResource,] imgfilt, img, kernel, border)
```

特定の `border` を指定するか、または

```
imfilter!(imgfilt, img, kernel, [Algorithm.FIR()])
```

でデフォルトのパディングを使用します。

`inds` が指定されている場合、`inds` のドメイン内のインデックスを持つ `imgfilt` の要素のみが計算されます。これは、より大きな領域にパディングを施し、次の各段階で必要な/明確に定義された領域に対してのみ結果を計算する「カスケードFIRフィルタ」に特に便利です。

参照: [`imfilter`](@ref).
