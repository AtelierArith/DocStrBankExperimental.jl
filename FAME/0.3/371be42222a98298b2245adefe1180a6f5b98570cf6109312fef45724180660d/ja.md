```
fame(io, command::String)
fame(command::String; quiet=false)
```

FAMEコマンド`command`を実行し、出力を`io`または画面に書き込みます。`io`が指定されていない場合、出力は`quiet=true`で抑制できます。
