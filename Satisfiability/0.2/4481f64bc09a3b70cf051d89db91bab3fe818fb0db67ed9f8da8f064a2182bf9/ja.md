```
send_command(pstdin::Base.Pipe, pstdout::Base.Pipe, cmd::String; is_done=nested_parens_match, timeout=Inf, line_ending='
```

')

新しいプロセスでソルバーを開き、in、out、およびerrパイプを使用します。Base.processを使用します。正確な実装を確認するにはソースコードを確認してください。 ```
