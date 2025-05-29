```
icellfound=gFindBruteForce!(xref,cellfinder,p; icellstart=1,eps=1.0e-14)
```

点 `p` を含むセルをセル番号 `icellstart` から検索します。

見つかった場合はセル番号を返し、見つからなかった場合はゼロを返します。戻り値として、xref には点のバリセントリック座標が `dim+1, 1...dim` の順序で含まれます。

!!! warning
    現在、単体グリッドのみに実装されています。

