```
FileSource(url::String, hash::String; filename::String = basename(url))
```

インターネットから`url`で指定されたリモートファイルをダウンロードするために指定します。`hash`はファイルの64文字のSHA256チェックサムです。

ビルダー環境では、ファイルは`${WORKSPACE}/srcdir`に、元のURLのベース名と同じ名前で保存されます。ただし、キーワード引数`filename`が指定されている場合はその限りではありません。
