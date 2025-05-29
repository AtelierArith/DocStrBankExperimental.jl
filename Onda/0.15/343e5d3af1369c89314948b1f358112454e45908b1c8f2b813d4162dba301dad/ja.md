```
LPCMZstFormat(lpcm::LPCMFormat; level=3)
LPCMZstFormat(info; level=3)
```

`LPCMZstFormat<:AbstractLPCMFormat` インスタンスを返します。このインスタンスは、OndaのデフォルトのインタリーブされたLPCMフォーマットを `zstd` で圧縮したものに対応しています。このフォーマットは、"lpcm.zst" 拡張子を持つサンプルデータファイルに対して仮定されています。

`level` キーワード引数は、`zstd` コマンドラインユーティリティによって文書化された対応するフラグと同じ圧縮レベルパラメータを設定します。

詳細については https://facebook.github.io/zstd/ を参照してください。
