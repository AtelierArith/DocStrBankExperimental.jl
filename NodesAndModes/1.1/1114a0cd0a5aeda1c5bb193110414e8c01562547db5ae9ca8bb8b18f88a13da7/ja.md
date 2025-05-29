```
nodes(elem::AbstractElemShape,N)
```

次数Nの補間ノードを計算します。エッジノードは(N+1)-点ロバット点と一致します。elem = Tet(), Pyr(), Tri()のデフォルトルーチンです。

Quad(), Hex(), Wedge()要素の場合、nodes(...)は低次元ノードのテンソル積を使用して構築された補間点を返します。
