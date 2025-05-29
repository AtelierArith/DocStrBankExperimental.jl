```julia
mmd(MF, a, b; ...)
mmd(MF, a, b, N; ...)
mmd(MF, a, b, N, M; ...)
mmd(MF, a, b, N, M, threads; bw)

```

MMDの不均衡（すなわち「距離」）測定は、二つの信念間のカーネルヒルベルト埋め込みに基づいています。

ノート：

  * これは、インプレースの`mmd!`関数へのラッパーです。

関連

mmd!, ker
