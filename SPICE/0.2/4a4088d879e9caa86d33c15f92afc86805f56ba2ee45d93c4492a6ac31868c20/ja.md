```
spksfs(body, et)
```

読み込まれたSPKファイルを検索して、指定された天体と時間に適用可能な最も優先度の高いセグメントを見つけます。

### 引数

  * `body`: 天体ID
  * `et`: エフェメリス時間

### 出力

セグメントが見つからなかった場合は`nothing`を返し、見つかった場合は次の要素からなるタプルを返します：

  * `handle`: 適用可能なセグメントを含むファイルのハンドル
  * `descr`: 適用可能なセグメントの記述
  * `ident`: 適用可能なセグメントの識別子

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spksfs_c.html)
