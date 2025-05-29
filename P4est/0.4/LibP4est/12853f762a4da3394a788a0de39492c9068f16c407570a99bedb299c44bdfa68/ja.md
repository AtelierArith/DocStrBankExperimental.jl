```
sc_package_lock(package_id)
```

pthreadミューテックスロックを取得します。–enable-pthreadなしで構成されている場合、この関数は何もしません。この関数の後には、対応するsc*package*unlockが必要です。

### パラメータ

  * `package_id`:[in] 未定義のパッケージの場合は-1、またはsc*package*registerから返されたid。値に応じて、適切なミューテックスが選択されます。したがって、異なるpackage_idでロック呼び出しを重複させることができます。

### プロトタイプ

```c
void sc_package_lock (int package_id);
```
