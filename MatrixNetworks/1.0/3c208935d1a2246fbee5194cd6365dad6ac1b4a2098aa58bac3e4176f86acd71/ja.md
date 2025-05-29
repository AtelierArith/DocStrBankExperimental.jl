## DIRCLUSTERCOEFFS

```
有向グラフのクラスタリング係数を計算します。
cc = dirclustercoeffs(A) は有向クラスタリング係数を返します
（これは無向グラフのクラスタリング係数を一般化したもので、
したがってこの関数を無向グラフに対して呼び出すと、
clustercoeffsと同じ結果が得られますが、効率は劣ります。）

この関数はFagioloのアルゴリズムを実装しています。 Phys Rev. E. 
76026107 (doi:10:1103/PhysRevE.76.026107)。  

(cc,cccyc,ccmid,ccin,ccout,nf) = dirclusteringcoeffs(A) は、サイクル、
三角形の中間、三角形の内側、外側に対応するクラスタリング係数の
異なる成分を返します。 上記のメトリックでカウントされるさまざまな
タイプの三角形の説明については原稿を参照してください。
```

## Functions

  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool)
  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64})
  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool,normalized::Bool)

## Example

```
(A,xy,labels) = load_matrix_network_metadata("celegans")
(cc, cccyc, ccmid, ccin, ccout, nf) = dirclustercoeffs(A, true, true)
(maxval, maxind) = findmax(cc)
labels[maxind]
```
