```
sauterschwab_parameterized(integrand, method::SauterSchwabStrategy)
```

相互作用積分を[1]で導入された数値積分を使用して計算します。

ここで、`integrand`は、積分領域を定義する2つの三角形のパラメトリック領域への積分関数のプルバックです。

第二引数の'strategy'は、三角形の場合は次のいずれかの型のオブジェクトです。

```
- `CommonFace`
- `CommonEdge`
- `CommonVertex`
- `PositiveDistance`
```

四角形の場合は次のいずれかの型のオブジェクトです。

```
- `CommonFaceQuad`
- `CommonEdgeQuad`
- `CommonVertexQuad`
```

これは、積分領域を定義する2つのパッチの構成に応じています。これらのクラスのコンストラクタは、最終的な長方形（ξ,η）積分領域の4つの軸に沿った数値積分点の数を定義する単一の引数`acc`を取ります（[1]、Ch 5を参照）。

ここでは、平面三角形の表現として次を使用します。

```
x = x[3] + u*(x[1]-x[3]) + v*(x[2]-x[3])
```

ここで、`u`は0から1まで、`v`は0から1-`u`までの範囲です。このパラメータ領域と表現は、[1]で使用されているものとは異なります。

[1] Sauter. Schwwab, 'Boundary Element Methods', Springer Berlin Heidelberg, 2011
