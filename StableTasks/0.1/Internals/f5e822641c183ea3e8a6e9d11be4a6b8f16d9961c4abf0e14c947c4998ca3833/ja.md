```
@spawn [:default|:interactive] expr
```

`Threads.@spawn`に似ていますが、型が安定しています。`Task`を作成し、指定されたスレッドプール（デフォルトは`:default`スレッドプール）で利用可能なスレッドで実行されるようにスケジュールします。
