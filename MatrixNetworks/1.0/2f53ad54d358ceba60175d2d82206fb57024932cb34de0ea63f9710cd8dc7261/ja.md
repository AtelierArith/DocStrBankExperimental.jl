## CSRTOSPARSE

```
圧縮スパース行列からスパース行列Aに変換します。
Juliaのスパース関数に供給する配列を返します。
```

## 関数

  * (nzi,nzj,nzv) = csr*to*sparse{T}(rp::Vector{Int64},ci::Vector{Int64},ai::Vector{T})
  * (nzi,nzj,nzv) = csr*to*sparse{T}(rp::Vector{Int64},ci::Vector{Int64},ai::Vector{T},nrows::Int64)

## 例

```
i = [1;2;3]
j = [3;4;4]
v = [8;9;10]
(rp,ci,ai,m) = sparse_to_csr(i,j,v)
(nzi,nzj,nzv) = csr_to_sparse(rp,ci,ai)
A = sparse(nzi,nzj,nzv,length(rp)-1,maximum(ci))
B = csr_to_sparse_matrix(rp,ci,ai)
isequal(A,B)
```
