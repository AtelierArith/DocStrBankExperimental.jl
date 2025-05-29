```
overlay!(path::Path, oversty::Style, metadata::DeviceLayout.Meta; i::Int=length(path))
```

スタイル `oversty` をレイヤー `metadata` に適用し、`path[i]` のセグメントの上に重ねます。

デフォルトでは、オーバーレイは最も最近のセグメントに適用されます。

オーバーレイは一般的に「装飾」としてカウントされます。たとえば、`refs(path)` には表示されますが、`elements(path)` には表示されません。オーバーレイは `undecorated(sty)` によって削除され、`straight!` のようなメソッドで `Path` を続ける際のデフォルトスタイルを選択する際には無視されます。

オーバーレイスタイルは、隣接するスタイルを見てテーパースタイルを解決できないため、一般的な `Paths.Taper` であってはなりません。

`attach!` の後に `overlay!` を使用することができ、その場合、オーバーレイはアタッチメントを保持する `DecoratedStyle` の基礎となるスタイルに適用されます。
