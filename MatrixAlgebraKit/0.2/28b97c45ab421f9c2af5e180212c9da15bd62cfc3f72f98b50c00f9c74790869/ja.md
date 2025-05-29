```
LAPACK_HouseholderQR(; blocksize, positive = false, pivoted = false)
```

アルゴリズムのタイプは、ハウスホルダー反射を使用して行列のQR分解を計算するための標準LAPACKアルゴリズムを示します。特定のLAPACK関数は、キーワード引数を使用して制御できます。つまり、`blocksize > 1`の場合は`?geqrt`が選択されます。`blocksize == 1`の場合、`pivoted == false`であれば`?geqrf`が選択され、`pivoted == true`であれば`?geqp3`が選択されます。キーワード`positive=true`を使用すると、`R`の対角要素が非負であることを保証できます。
