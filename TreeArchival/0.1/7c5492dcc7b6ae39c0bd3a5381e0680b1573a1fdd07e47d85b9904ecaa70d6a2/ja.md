```
treehash(source_file::String; compressor::String = detect_compressor(source_file),
                              ignore_unstable_formats::Bool = false)
```

`source_file`で指定されたアーカイブのツリーハッシュを計算し、最初の数バイトを調べることで圧縮タイプを自動的に決定します。 バイトのベクターを返します。

圧縮タイプを自動的に決定できない場合は、エラーをスローします。

`source_file`が`.zip`ファイルの場合、`ignore_unstable_formats`が`true`に設定されていない限り、エラーをスローします。それでも、警告が表示されます。
