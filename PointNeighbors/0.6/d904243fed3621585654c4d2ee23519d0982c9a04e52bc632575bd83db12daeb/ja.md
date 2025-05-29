```
default_backend(x)
```

配列 `x` に対して推奨されるバックエンドを選択します。これにより、CPU と GPU の配列の両方で動作する汎用コードを書くことができます。

現在、CPU 配列のデフォルトバックエンドは `PolyesterBackend()` です。GPU 配列の場合、対応する `KernelAbstractions.Backend` が返されます。
