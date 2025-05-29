```
position(x::Union{AbstractGroup, AbstractIrrep})
```

`x` に関連付けられた位置がある場合はそれを返し、関連付けられた位置がない場合は `nothing` を返します。

適用可能なケースには `LittleGroup`（関連付けられた **k**-ベクトルを返す）や `SiteGroup`（関連付けられたワイコフ位置を返す）、およびそれに関連する不変表現タイプ（`LGIrrep` と `SiteIrrep`）が含まれます。
