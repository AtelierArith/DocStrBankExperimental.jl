## SPARSETOCSR

```
スパース行列を圧縮行ストレージ配列に変換し、
行ポインタ (rp)、列インデックス (ci)、および値インデックス (ai) 配列を返します
行列 A の圧縮スパース表現 (またはその三重形式ストレージ) の
```

## 関数

  * (rp,ci,ai,m) = sparse*to*csr{T}(A::SparseMatrixCSC{T,Int64})
  * (rp,ci,ai,m) = sparse*to*csr{T}(nzi::Array{Int64,1},nzj::Array{Int64,1},nzv::Array{T,1})

## 例

```
i = [1;2;3]
j = [3;4;4]
v = [8;9;10]
(rp,ci,ai,m) = sparse_to_csr(i,j,v)
```
