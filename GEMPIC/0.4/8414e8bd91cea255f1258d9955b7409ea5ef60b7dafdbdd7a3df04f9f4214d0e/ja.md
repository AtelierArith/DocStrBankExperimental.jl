```
compute_e_from_j(e, solver, current, component)
```

j*iを時間間隔で積分してE*iを計算します。弱いアンペールの定式化を使用します。

  * solver : マクスウェルソルバークラス
  * current : 時間間隔で積分された電流の成分
  * component : 計算されるEフィールドの成分
  * e : 更新された電場
