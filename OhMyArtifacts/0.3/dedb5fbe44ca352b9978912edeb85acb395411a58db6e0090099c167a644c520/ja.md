```
create_my_artifact(f::Function)
```

`f(working_dir)`を呼び出すことでアーティファクトを作成します。`f`は`working_dir`にファイルを作成/配置/ダウンロードする関数です。`f`はファイル/ディレクトリへのパスを返すか、`nothing`を返す必要があります。`f`が`nothing`を返す場合、`working_dir`内のすべてのものがキャッシュされます。`f`がパスを返す場合、そのパスは`working_dir`内でなければなりません。
