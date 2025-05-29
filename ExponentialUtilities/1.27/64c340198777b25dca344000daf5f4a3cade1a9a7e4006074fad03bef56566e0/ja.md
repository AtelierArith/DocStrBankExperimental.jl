```
arnoldi(A,b[;m,tol,opnorm,iop]) -> Ks
```

`m` 回のアーノルディ反復を実行して、クリロフ部分空間 K_m(A,b) を取得します。

n x (m + 1) 基底ベクトル `getV(Ks)` と (m + 1) x m 上ヘッセンベルグ行列 `getH(Ks)` は、再帰式によって関連付けられています。

```
v_1=b,\quad Av_j = \sum_{i=1}^{j+1}h_{ij}v_i\quad(j = 1,2,\ldots,m)
```

`iop` は不完全直交化手順の長さを決定します [^1]。デフォルト値の 0 はフルアーノルディを示します。対称/Hermitian な `A` の場合、`iop` は無視され、代わりにランチョスアルゴリズムが使用されます。

出力に関する詳細は `KrylovSubspace` を参照してください。

`norm(v_j) < tol * opnorm` の場合、ハッピーブレイクダウンが発生し、この場合、`Ks` の次元は `m` より小さくなります。

[^1]: Koskela, A. (2015). Approximating the matrix exponential of an advection-diffusion operator using the incomplete orthogonalization method. In Numerical Mathematics and Advanced Applications-ENUMATH 2013 (pp. 345-353). Springer, Cham.
