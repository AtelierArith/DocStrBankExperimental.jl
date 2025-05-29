```
cm_reduce!(matrix::SparseMatrix, psetvec::Vector{Int};
           [returnbasis::Bool],[returntm::Bool])
```

接続行列を計算します。

`matrix` が上三角であり、`psetvec` に従ってフィルタリングされていると仮定します。引数 `matrix` を変更します。

# 戻り値:

  * `cmatrix`: 接続行列
  * `cmatrix_cols`: 境界における接続行列の列
  * `basisvecs` (オプション): 引数 `returnbasis=true` が指定されている場合、計算された基底に関する情報を返します。`basisvecs` の k 番目のエントリは、k 番目の基底ベクトルを構成する列を含むベクトルであり、これは列 `cmatrix_cols[k]` に対応します。
  * `tmatrix` (オプション): 引数 `returntm=true` が `returnbasis=true` に加えて指定されている場合、関数は `basisvecs` の代わりに完全な変換行列を返します。この場合、`basicvecs` は返されません。
