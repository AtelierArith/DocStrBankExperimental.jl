```
sc_package_unlock(package_id)
```

pthreadミューテックスロックを解除します。–enable-pthreadなしで構成されている場合、この関数は何もしません。この関数は、対応するsc*package*lockの後に呼び出す必要があります。

### パラメータ

  * `package_id`:[in] 未定義のパッケージの場合は-1、またはsc*package*registerから返されたid。値に応じて、適切なミューテックスが選択されます。したがって、異なるpackage_idでロック呼び出しを重複させることができます。

### プロトタイプ

```c
void sc_package_unlock (int package_id);
```
