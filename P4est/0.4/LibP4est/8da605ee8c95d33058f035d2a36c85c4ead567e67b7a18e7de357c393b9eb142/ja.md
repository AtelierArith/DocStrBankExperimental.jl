```
p4est_is_balanced(p4est_, btype)
```

森林がバランスが取れているかどうかを確認します。

この関数はゴーストレイヤーを構築し、完了したらそれを破棄します。

### パラメータ

  * `p4est`:[in] テストされる `p4est`。
  * `btype`:[in] バランスタイプ（面、コーナー、またはデフォルト、フル）。

### 戻り値

バランスが取れていればtrue、そうでなければfalseを返します。

### プロトタイプ

```c
int p4est_is_balanced (p4est_t * p4est, p4est_connect_type_t btype);
```
