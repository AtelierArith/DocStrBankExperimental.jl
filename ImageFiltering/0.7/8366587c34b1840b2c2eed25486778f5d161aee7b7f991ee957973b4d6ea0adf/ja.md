```
imfilter!(imgfilt, img, kernel, [border="replicate"], [alg])
imfilter!(r, imgfilt, img, kernel, border::Pad)
imfilter!(r, imgfilt, img, kernel, border::NoPad, [inds=axes(imgfilt)])
```

配列 `img` をカーネル `kernel` でフィルタリングし、その結果を `imgfilt` に格納します。

`imgfilt` のインデックスは、フィルタリングされた画像が計算される領域を決定します。この事実を利用して、特定の関心領域を選択することができますが、入力 `img` がまだパディングされる可能性があることに注意してください。あるいは、計算したい `imgfilt` のインデックス `inds` を明示的に提供し、`NoPad` 境界条件を使用します。そのような場合、適切なパディングを供給する責任があります：出力を計算するために必要なすべての位置で `img` はインデックス可能でなければなりません。この構文は FIR フィルタリングに最も適しています。特に、IIR フィルタリングは、全体の配列をフィルタリングすることに関して一貫性のない結果をもたらす可能性があります。

参照: [`imfilter`](@ref).
