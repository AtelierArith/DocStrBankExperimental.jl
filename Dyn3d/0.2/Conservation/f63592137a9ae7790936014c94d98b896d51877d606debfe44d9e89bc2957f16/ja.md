```
work!(dict,bd,λ,k)
```

  * `dict` : エネルギー保存の項の構造。 "edam", "edam*temp", "elag", "elag*temp", "ekin", "espr", "egra" のキーを含む
  * `bd` : 現在の BodyDyn 構造
  * `λ` : ジョイントの制約された自由度に対する体による力
  * `k` : k-1 は rk スキームの現在のステージを表す

アクティブに指定された動きの下でボディ-ジョイントシステムがある場合、rk スキームのタイムステップ内の1つのステージでラグランジュ乗数によって行われた仕事を計算します。また、1つのステージ内でダンパーによって抽出されたエネルギーも計算します。この関数は、RK スキームの各ステージで呼び出す必要があります。
