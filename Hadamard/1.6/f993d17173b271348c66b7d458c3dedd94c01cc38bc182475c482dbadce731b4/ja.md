```
fwht(X, dims=1:ndims(X))
```

配列 `X` の次元 `dims` に沿った高速ウォルシュ-ハダマード変換 (WHT) を返します（整数、タプル、または次元の配列で、デフォルトはすべての次元）。 変換された次元に沿ったサイズは、2の累乗のみがサポートされています。 結果はシーケンシー順序で返されます。

私たちの WHT は正規化されており、前方変換には `1/n` の係数があり（ここで `n` は変換された次元の積）、逆 WHT にはスケーリング係数がありません。
