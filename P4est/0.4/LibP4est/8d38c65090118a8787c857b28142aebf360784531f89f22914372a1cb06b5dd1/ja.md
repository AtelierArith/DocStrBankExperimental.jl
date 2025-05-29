```
p4est_connectivity_new_byname(name)
```

事前定義されたカタログから接続構造を作成します。

### パラメータ

  * `name`:[in] connectivity*new** 関数を呼び出します。 brick23 brick (2, 3, 0, 0) corner corner cubed cubed disk disk moebius moebius periodic periodic pillow pillow rotwrap rotwrap star star unit unitsquare

### 戻り値

name が定義されている場合は初期化された接続を返し、そうでない場合は NULL を返します。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_byname (const char *name);
```
