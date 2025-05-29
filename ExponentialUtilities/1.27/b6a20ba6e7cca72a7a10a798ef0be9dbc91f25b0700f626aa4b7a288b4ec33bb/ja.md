```
phiv(t,A,b,k;correct,kwargs) -> [phi_0(tA)b phi_1(tA)b ... phi_k(tA)b][, errest]
```

Krylovを使用して行列-phi-ベクトル積を計算します。 `k` >= 1。

phi関数は次のように定義されます。

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

Krylov部分空間は`arnoldi`を使用して構築され、Hessenberg行列に対して`phiv_dense`が呼び出されます。 `correct=true`の場合、phi*0からphi*k-1は最後のArnoldiベクトルv_m+1を使用して更新されます[^1]。 `errest=true`の場合、最後から2番目のphiの追加の誤差推定も返されます。追加のキーワード引数については、`arnoldi`を参照してください。

phiv(t,Ks,k;correct,kwargs) -> [phi*0(tA)b phi*1(tA)b ... phi_k(tA)b][, errest]

事前に構築されたKrylov部分空間を使用して行列-phi-ベクトル積を計算します。

[^1]: Niesen, J., & Wright, W. (2009). A Krylov subspace algorithm for evaluating the φ-functions in exponential integrators. arXiv preprint arXiv:0907.4631. Formula (10).
