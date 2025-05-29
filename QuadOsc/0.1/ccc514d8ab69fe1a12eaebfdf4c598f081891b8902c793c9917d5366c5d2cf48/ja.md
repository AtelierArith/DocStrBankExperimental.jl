```
quadosc(fn, a, Inf, fnzeros; ...)
```

関数 `fn(x)` を `a` から `Inf` まで積分します。関数 `fnzeros(n)` は整数 `n` を受け取り、`fn(fnzeros(n)) == 0` となるように定義されています。このアルゴリズムは、連続するゼロの間で積分を行い、交互級数を加速することによって動作します。

引数 `pren` は、級数加速を適用する前に積分する区間の数です。

`atol` と `rtol` は収束を決定するための絶対および相対許容誤差を指定します。

`order` は [QuadGK](https://github.com/JuliaMath/QuadGK.jl) パッケージの `quadgk()` に渡されます。

`nconvergences` は収束が宣言される前の反復回数です。

詳細については `?QuadOsc.accel_cohen_villegas_zagier` を参照してください。
