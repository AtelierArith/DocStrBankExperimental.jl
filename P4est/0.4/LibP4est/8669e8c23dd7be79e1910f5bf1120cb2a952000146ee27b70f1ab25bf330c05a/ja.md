```
p8est_is_balanced(p8est_, btype)
```

森林がバランスが取れているかどうかを確認します。

この関数はゴーストレイヤーを構築し、完了したらそれを破棄します。

### パラメータ

  * `p8est`:[in] テストされる `p8est`。
  * `btype`:[in] バランスタイプ（面、エッジ、コーナー、またはデフォルト、フル）。

### 戻り値

バランスが取れていればtrueを、そうでなければfalseを返します。

### プロトタイプ

```c
int p8est_is_balanced (p8est_t * p8est, p8est_connect_type_t btype);
```
