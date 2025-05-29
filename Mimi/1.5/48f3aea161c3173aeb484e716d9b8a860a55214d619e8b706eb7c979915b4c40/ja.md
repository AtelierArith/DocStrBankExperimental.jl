```
is_last(ts::VariableTimestep)
```

`ts`が実行される最後のタイムステップである場合はtrueを返し、そうでない場合はfalseを返します。`ts`に対して`next_timestep`を実行することができますが、最終タイムステップはまだ実行されていないことに注意してください。
