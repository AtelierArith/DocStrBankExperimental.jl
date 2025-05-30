```
@einsum tns[idxs...] <<op>>= ex...
```

`op`をテンソル`tns`にインデックス`idxs`を適用し、式`ex`のテンソルに対して計算するeinsum式を構築します。結果は変数`tns`に格納されます。

`ex`は、関数呼び出しと`tns[idxs...]`の形のテンソル参照からなる任意のポイントワイズ式である可能性があります。ここで、`tns`と`idxs`はシンボルです。

`<<op>>`演算子は、式`ex`の要素型に対して定義されている任意の二項演算子であることができます。

einsumは、`tns[idxs...] <<op>>= ex...`のポイントワイズ式を、`tns`と`ex`のテンソルのインデックス値のすべての組み合わせに対して評価します。

以下はいくつかの例です：

```
@einsum C[i, j] += A[i, k] * B[k, j]
@einsum C[i, j, k] += A[i, j] * B[j, k]
@einsum D[i, k] += X[i, j] * Y[j, k]
@einsum J[i, j] = H[i, j] * I[i, j]
@einsum N[i, j] = K[i, k] * L[k, j] - M[i, j]
@einsum R[i, j] <<max>>= P[i, k] + Q[k, j]
@einsum x[i] = A[i, j] * x[j]
```
