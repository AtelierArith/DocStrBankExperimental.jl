```
function Integrator(dt, i=1.0, x0=0.0)
```

外部リセットを持つ離散積分器のコンストラクタ。

## パラメータ

  * dt: 時間ステップ [s]
  * i: 積分定数
  * x0: 初期および最終出力

## 戻り値

  * `Integrator`型の新しい構造体
