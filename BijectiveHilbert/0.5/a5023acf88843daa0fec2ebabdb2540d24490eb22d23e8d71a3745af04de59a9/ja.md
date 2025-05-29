```
FaceContinuous(b::Int, n::Int)
FaceContinuous(::Type{T}, b::Int, n::Int)
```

`n` 次元の場合、このヒルベルト曲線で `b` ビットの精度を使用します。型 `T` を指定すると、これがヒルベルトエンコーディングの型として使用されます。指定しない場合、`n*b` ビットを保持できる最小の符号なし整数がヒルベルトインデックスデータ型として使用されます。

これは、Lawder によって提示された Butz アルゴリズムです。Haverkort2017 はそれが面連続であると言っています。コードは lawder.c にあります。元の論文には誤りがあり、Lawder は彼のウェブサイトに訂正を掲載しました。http://www.dcs.bbk.ac.uk/~jkl/publications.html
