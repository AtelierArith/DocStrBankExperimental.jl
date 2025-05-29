```
struct DmrgObserver
DmrgObserver(sim, measurements, period, tol)
```

dmrgのオブザーバーで、指定された周期ごとに測定を行い、エネルギーの改善がtolより小さくなると停止します。
