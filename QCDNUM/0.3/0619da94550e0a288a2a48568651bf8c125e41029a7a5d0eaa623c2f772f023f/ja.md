```
qcdnum_lock()::AbstractLock
```

QCDNUM操作のためのグローバルロックを取得します。

QCDNUM Fortranパッケージ自体はスレッドセーフではないため、QCDNUM.jlはFortranライブラリへの並列呼び出しに対して保護するためにグローバルロックを使用します。
