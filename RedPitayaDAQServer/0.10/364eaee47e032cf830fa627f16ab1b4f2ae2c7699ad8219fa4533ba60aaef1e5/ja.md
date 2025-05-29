```
execute!(rp::RedPitaya, batch::ScpiBatch)
```

指定されたバッチのすべてのコマンドを実行します。コマンドの順序で結果の配列を返します。要素は、コマンドに戻り値がない場合は `nothing` です。
