```
archive(source_dir::String, output_path::String, compressor::String;
        stderr_out = stderr)
```

`source_path` から読み込み、最初の数バイトを調べることで圧縮タイプを自動的に判断し、解凍された結果を `output_dir` に書き込みます。

圧縮タイプを自動的に判断できない場合は、エラーをスローします。
