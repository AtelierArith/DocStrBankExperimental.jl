```
rebuild_model(mc; calibration = false)
```

モデルを再構築します。通常、キャリブレーション方程式なしでスリムなモデルを作成するために使用されます。

### 引数:

  * `mc`: モデルコンテナ
  * `calibration`: キャリブレーション方程式を含める

## 戻り値:

更新されたモデルコンテナ

### 例:

$$
julia rebuild_model!(mc)
$$
