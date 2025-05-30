```
contents(gp::GridPosition; exact::Bool = false)
```

`GridPosition` `gp` に格納されている `Span` と `Side` に `GridLayout` に配置されたすべてのオブジェクトを取得します。`exact == true` の場合、要素は `Span` と正確に一致する場合のみ含まれ、それ以外の場合はスパンされたレイアウト領域内に含まれていることもできます。
