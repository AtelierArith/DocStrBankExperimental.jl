```
set_vset_pc(cvi::CalcVSetIn, v_set_pc, force)
```

## パラメータ:

  * force:      測定されたテザー力 [N]
  * `v_set_pc`: 手動操作または長さでの駐車中のみ使用されます。もし `nothing` の場合、             `v_set_in` は力の関数として計算されます。

## 戻り値:

  * 何も返さない
