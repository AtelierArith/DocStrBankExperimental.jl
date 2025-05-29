```
 maybewatertight(this::SimplexGridBuilder; bregions=nothing)
```

bregionsに属する境界領域のファセットが水密であるかどうかを確認します。これはいくつかのヒューリスティックに基づいており、否定的な回答のみが決定的です。
