```
map = read_maps(snpmapfile,qtlmapfile,qtleffectfile; ntr=0)
```

3つのマップと効果ファイルを読み込み、単一のマップオブジェクト `QMSimMap` を作成します。 `ntr>0` の場合、`ntr` 特性のQTL効果を持つマップオブジェクトが返されます。この場合、特性1のためにQTL効果が読み込まれ、他の特性にはゼロのQTL効果が割り当てられます。
