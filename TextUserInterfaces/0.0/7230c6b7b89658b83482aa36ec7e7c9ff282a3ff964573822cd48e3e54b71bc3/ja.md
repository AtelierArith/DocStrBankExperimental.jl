```
function update_view(win::Window; force::Bool = false)
```

ウィンドウ `win` のビューをバッファから内容をコピーすることで更新します。ビューを更新する必要がない場合（`view_needs_update` を参照）、何も行われません。キーワード `force` が `true` の場合、コピーは常に行われます。

# 戻り値

ビューが更新された場合は `true` を、そうでない場合は `false` を返します。
