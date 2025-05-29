```
Sequence{T, S}
Sequence(schedules, step_sizes)
Sequence(schedule1 => step1, schedule2 => step2, ...)
```

スケジュールのシーケンス。 このスケジュールの出力は、各スケジュールが `step_sizes` の各ステップサイズに対して評価される `schedules` の連結です。

`schedules` はスケジュールだけでなく、数値のベクトルでもあることに注意してください。

# 引数

  * `schedules`: スケジュールまたは数値のベクトル
  * `step_sizes`: 各スケジュールの反復長のベクトル
