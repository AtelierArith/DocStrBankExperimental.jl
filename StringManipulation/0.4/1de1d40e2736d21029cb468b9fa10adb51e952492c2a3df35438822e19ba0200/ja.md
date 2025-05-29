```
replace_default_background(str::AbstractString, new_background::AbstractString) -> String
```

`str`のデフォルトの背景を`new_background`のものに置き換えます。後者は背景を設定する有効なANSIエスケープシーケンスで表現されている必要があります。

内部的に、この関数は装飾をリセットするANSIシーケンス（`[0m`）とデフォルトの背景を設定するANSIシーケンス（`[49m`）を新しい背景に置き換え、他のすべてのサポートされている装飾を保持します。
