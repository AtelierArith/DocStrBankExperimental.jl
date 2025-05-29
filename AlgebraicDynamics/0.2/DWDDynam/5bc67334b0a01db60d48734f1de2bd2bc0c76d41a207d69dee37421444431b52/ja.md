```
ContinuousMachine{T}(ninputs, nstates, noutputs, f, r)
```

指向性のある開放連続システムです。動的関数 `f` はODE $\dot u(t) = f(u(t),x(t),p,t)$ を定義し、ここで $u$ は状態、$x$ は外生変数を表します。

読み出し関数 `r` は状態、パラメータ、時間に依存する可能性があるため、形式は $r(u,p,t)$ でなければなりません。省略された場合、$r=u$ となります。
