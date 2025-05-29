```
geodesic(tree1::T, tree2::T)::Float64 where T<:GeneralNode
```

この関数は、2つの木の間の測地線距離を計算して返します。

  * `tree1` : 最初の木の根ノード。
  * `tree2` : 2番目の木の根ノード。
  * `verbose`: 'true'に設定すると、共通のエッジと葉の寄与を印刷します。

測地線距離を計算するGTPアルゴリズムは、Megan OwenとJ. Scott Provanによる同じアルゴリズムのJava実装から密接に適応されています。

(M. Owen and J.S. Provan. A fast algorithm for computing geodesic distances in tree space.  IEEE/ACM Transactions on Computational Biology and Bioinformatics, 8:2-13, 2011.) 
