```
icellfound=GFindLocal!(xref,cellfinder,p; icellstart=1,eps=1.0e-14, trybrute=true)
```

点 `p` を含むセルをセル番号 `icellstart` から探します。

見つかった場合はセル番号を返し、見つからなかった場合はゼロを返します。 `trybrute==true` の場合は、あきらめる前に [`gFindBruteForce!`](@ref) を試みます。戻り値として、xref には次のシーケンス `dim+1, 1...dim` における点のバリセントリック座標が含まれます。

!!! warning
    現在、単体グリッドのみに実装されています。

