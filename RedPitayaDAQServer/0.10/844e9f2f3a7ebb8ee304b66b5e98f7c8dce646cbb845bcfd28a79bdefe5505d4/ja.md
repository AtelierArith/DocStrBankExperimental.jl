```
execute!(rpc::RedPitayaCluster, batch::ScpiBatch)
```

指定されたバッチのすべてのコマンドを実行します。コマンドの順序で結果の配列を返します。

結果配列の各要素は、RedPitayaの戻り値を含む配列です。内部配列の要素は、コマンドに戻り値がない場合は`nothing`になります。
