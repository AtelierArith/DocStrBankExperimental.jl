```
sc_package_unregister(package_id)
```

SCからソフトウェアパッケージを登録解除します。この関数は、追加のスレッドが終了した後にのみ呼び出す必要があります。

### プロトタイプ

```c
void sc_package_unregister (int package_id);
```
