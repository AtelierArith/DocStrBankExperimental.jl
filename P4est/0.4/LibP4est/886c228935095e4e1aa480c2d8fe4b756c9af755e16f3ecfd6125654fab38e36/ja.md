```
p8est_connectivity_new_byname(name)
```

事前定義されたカタログから接続構造を作成します。

### パラメータ

  * `name`:[in] connectivity*new** 関数を呼び出します。 brick235 brick (2, 3, 5, 0, 0, 0) periodic periodic rotcubes rotcubes rotwrap rotwrap shell shell sphere sphere twocubes twocubes twowrap twowrap unit unitcube

### 戻り値

name が定義されている場合は初期化された接続を返し、そうでない場合は NULL を返します。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_byname (const char *name);
```
