```
AliveCallback(analysis_interval=0, alive_interval=analysis_interval÷10)
```

シミュレーションがまだ実行中であることを示す安価なコールバックで、`alive_interval` の時間ステップごとに現在の時間などの情報を画面に印刷します。`analysis_interval ≂̸ 0` の場合、出力は `analysis_interval` の時間ステップごとに省略されます。
