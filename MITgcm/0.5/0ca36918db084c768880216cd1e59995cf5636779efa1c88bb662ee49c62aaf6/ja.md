```
build(config::MITgcm_config,options::String)
```

モデルを `genmake2`、`make depend`、および `make` を使用して構築しますが、`options` で別途指定されていない限りはそうします。`genmake2` および `make depend` コマンドは、`build/` フォルダー内のすべてのコードファイル、ヘッダーなどをリンクし、その後 `make` がモデルをコンパイルします。

（`MITgcm` に特化した気候モデルインターフェースの一部）
