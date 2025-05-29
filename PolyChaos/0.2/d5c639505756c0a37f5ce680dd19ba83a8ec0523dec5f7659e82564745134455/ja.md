```
rm_meixner_pollaczek(N::Int,lambda::Real,phi::Real)
rm_meixner_pollaczek(N::Int,lambda::Real)
```

パラメータ λ と ϕ を持つ単項 Meixner-Pollaczek 多項式のための `N` 再帰係数を生成します。これらは、重み関数 $w(t)=(2 \pi)^{-1} \exp{(2 \phi-\pi)t} |\Gamma(\lambda+ i t)|^2$ に対して $[-\infty,\infty]$ 上で直交します。

呼び出し `rm_meixner_pollaczek(n,lambda)` は `rm_meixner_pollaczek(n,lambda,pi/2)` と同じです。
