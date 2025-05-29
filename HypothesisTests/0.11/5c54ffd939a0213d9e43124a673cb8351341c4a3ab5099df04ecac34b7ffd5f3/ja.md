```
BreuschPaganTest(X, e)
```

ヘテロスケダスティシティのためのブレイシュ-パガンテストを計算します。

`X` は元のモデルからの回帰変数の行列で、`e` は残差のベクトルです。これは `WhiteTest(X, e, type = :linear)` と同等です。詳細については [`WhiteTest`](@ref) を参照してください。
