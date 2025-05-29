```
DowkerComplex(A,maxdensity=1)

これは、矩形行列 A のダウカー複体を返します。
この関数の通常の使用法は次のとおりです。

FS, GraphDensity=DowkerComplex(A);
または
FS, GraphDensity=DowkerComplex(A,maxdensity);

ここで、FS は FiltrationOfSimplicialComplexes の型です。
GraphDensity は長さ =F.depth の実数の配列であり、
各数 GraphDensity[i] はフィルトレーション内の単体複体 Δ_i におけるグラフ密度を表します。
```
