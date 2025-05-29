```
HeldTriangulation([rng]; shuffle=true)
```

ポリゴンのための高速産業用三角形分割（FIST）。

この三角形分割法は、有名なMapboxのEarcutライブラリの背後にある方法です。これは、穴のある複雑なn-gonに適応された耳クリッピングアルゴリズムに基づいています。時間計算量はO(n²)で、ここでnは頂点の数です。実際には、アルゴリズムに実装されたヒューリスティックのおかげで非常に効率的です。

オプション`shuffle`は、耳がクリッピングされる順序をシャッフルするために使用されます。これにより、三角形の質が向上し、非常に細長くなることがあります。オプションで、乱数生成器`rng`を指定できます。

## 参考文献

  * Held, M. 1998. [FIST: Fast Industrial-Strength Triangulation of Polygons](https://link.springer.com/article/10.1007/s00453-001-0028-4)
  * Eder et al. 2018. [Parallelized ear clipping for the triangulation and constrained Delaunay triangulation of polygons](https://www.sciencedirect.com/science/article/pii/S092577211830004X)
