```
DelayResourceSharer{T}(nports, nstates, f, portmap)
```

無向の開いた連続システム。動的関数 `f` は DDE $\dot u(t) = f(u(t),h(t),p,t)$ を定義し、ここで $h$ は解が計算される区間が始まる前のシステムの状態 $u$ の履歴を与える関数（通常は $t < 0$ の場合）です。`f` は $f(u,h,p,t)$ というシグネチャを持つべきであり、ここで $h$ は関数です。
