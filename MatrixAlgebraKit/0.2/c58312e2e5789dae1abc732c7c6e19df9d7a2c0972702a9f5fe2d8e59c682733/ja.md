```
LAPACK_HouseholderLQ(; blocksize, positive = false)
```

アルゴリズムタイプは、ハウスホルダー反射を使用して行列のLQ分解を計算するための標準LAPACKアルゴリズムを示します。特定のLAPACK関数は、キーワード引数を使用して制御できます。つまり、`blocksize > 1`の場合は`?gelqt`が選択され、`blocksize == 1`の場合は`?gelqf`が選択されます。キーワード`positive=true`を使用すると、`L`の対角要素が非負であることを保証できます。
