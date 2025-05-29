```
momentum!(dict,bd)
```

  * `dict` : エネルギー保存の項の構造。 "mlag", "mlag*temp", "mgra", "mgra*temp", "mkin" のキーを含む
  * `bd` : 現在の BodyDyn 構造

慣性フレームにおける全体の運動量を計算します。この関数は RK スキームの最終段階で一度だけ呼び出す必要があります。
