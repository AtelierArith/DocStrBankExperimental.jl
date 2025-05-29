```
exp(M::Rotations, p, X)
exp(M::OrthogonalMatrices, p, X)
exp(M::UnitaryMatrices, p, X)
```

指数写きのマップを計算します。すなわち、$X$がリー代数で表されているので、

```
exp_p(X) = p\mathrm{e}^X
```

サイズが異なる場合、例えば$n=2,3,4$のように、特化した実装があります。

使用されるアルゴリズムは、[GallierXu:2002](@cite)および[AndricaRohan:2013](@cite)で提案されたものの、より数値的に安定した形式です。
