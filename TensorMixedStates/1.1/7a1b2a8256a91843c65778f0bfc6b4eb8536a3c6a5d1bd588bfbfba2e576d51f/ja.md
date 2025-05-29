```
approx_W(evolver, t, ::State; options...)
approx_W(evolver, t, ::Simulation; options...)
```

与えられた次数での近似WIまたはWIIを使用した時間発展。`ApproxWObserver`も参照してください。

# オプション

  * `coefs`: 時間依存の発展のための係数
  * `n_symmetrize`: n_symmetrizeステップごとにエルミート化する（混合状態用）（修正なしの場合はデフォルト0）
  * `nsweeps`: ステップ数（時間ステップはt / nsweeps）
  * `order`: 近似の次数
  * `w`: WIまたはWIIのための1または2
  * `observer!`: 観測者（ApproxWObserverを参照）
  * `time_start`: 発展の開始時のシミュレーション時間
  * `limits`: MPS制約
