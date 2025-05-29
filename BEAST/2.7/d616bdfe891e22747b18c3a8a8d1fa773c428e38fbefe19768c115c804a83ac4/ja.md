```
real_inverse_z_transform(k, rho, N, X)
```

k 番目の逆 z 変換の項を返します。X[n+1] = conj(X[N-n]) が各 n に対して 1:(N-1) の範囲で成り立つと仮定されているため、Nmax = N/2+1 または (N+1)/2 (それぞれ N%2==0 または N%2==1 の場合) の項が X に使用されます。X は z 変換が z=rho*exp(2*im*pi*n/N) の点で評価された配列です。n の範囲は 0:(Nmax-1) です。
