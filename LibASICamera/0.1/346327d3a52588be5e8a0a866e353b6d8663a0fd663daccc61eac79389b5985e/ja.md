```
start_exposure(id::Integer, is_dark=false)
```

露出を開始します。すべての関連パラメータ（露出時間、ゲイン）は、事前に set*control*value(...) または e.g. set_gain(...) を呼び出すことで設定する必要があります。
