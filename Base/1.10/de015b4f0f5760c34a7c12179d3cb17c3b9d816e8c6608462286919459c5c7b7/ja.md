```
kill(p::Process, signum=Base.SIGTERM)
```

プロセスにシグナルを送信します。デフォルトではプロセスを終了させます。プロセスがすでに終了している場合は成功を返しますが、他の理由（例：権限不足）でプロセスの終了に失敗した場合はエラーをスローします。
