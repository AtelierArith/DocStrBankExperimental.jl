```
uniformize(Q, p0, k=2^10, t=0.0,
           method::Function=erlangization, args...)
```

近似 𝐩(t) = exp(t𝐐)𝐩(0) を均一化を使用して行います。パラメータ k は、近似されたプロセスで発生する遷移の速度を制御します。k が大きいほど、より良い近似が得られます。時間 𝑡 における状態の（正規化された）分布を返します。

デフォルトでは、エルランギゼーション/外部均一化を使用します。これは、硬い問題に対して最も堅牢であるようです。
