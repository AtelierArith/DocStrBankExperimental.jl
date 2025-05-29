```
build(config::MITgcm_config)
```

モデルを `genmake2`、`make depend`、および `make` を使用してビルドします。最初の2つは、モデルをコンパイルする前に `build/` フォルダー内のすべてのコードファイル、ヘッダーなどをリンクします。

注意：`config.inputs[:setup][:main][:exe]` が指定されている場合は、これをスキップします。
