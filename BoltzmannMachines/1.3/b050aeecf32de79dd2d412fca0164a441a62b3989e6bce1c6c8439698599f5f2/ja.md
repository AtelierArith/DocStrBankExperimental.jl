```
gibbssamplecond!(particles, bm, cond, nsteps)
```

`nsteps` ギブスサンプリングステップのために `bm` 内の `particles` に対して条件付きギブスサンプリングを行います。

インデックスベクトル `cond` でマークされた変数は、サンプリング中に `particles` の初期値に固定されます。この方法で、これらの変数に対して条件付きサンプリングが行われます。

関連情報: `Particles`, `initparticles`
