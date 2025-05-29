```
cpucycle_id()
```

CPUの[タイムスタンプカウンタ、TSC](https://en.wikipedia.org/wiki/Time_Stamp_Counter)を読み取り、`rdtscp`命令を使用してCPU idを直接実行します。この関数は`cpucycle()`に似ていますが、コードが異なる実行CPUに移動したかどうかを検出することも可能な命令を使用します。`cpucycle()`に関するコメントも同様に適用されます。
