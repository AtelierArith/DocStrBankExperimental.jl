```
cachefs(protocol::String="http") -> CachingFileSystem
```

`fsspec_cached.CachingFileSystem`を使用してキャッシングファイルシステムオブジェクトを作成します。`protocol`引数は使用される基盤となるファイルシステムプロトコルを設定し、デフォルトでは`"http"`に設定されています。

指定されたファイルシステムからファイルを読み書きするために使用できる新しい`CachingFileSystem`オブジェクトを返します。
