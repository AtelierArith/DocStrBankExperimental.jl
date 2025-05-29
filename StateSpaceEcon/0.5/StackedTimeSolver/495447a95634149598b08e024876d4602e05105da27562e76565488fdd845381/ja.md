```
dictoverlay(d1, d2)
```

2つの辞書をマージします。値が同じ頻度の[`TSeries`](@ref TimeSeriesEcon.TSeries)である共通のキーはオーバーレイされます。それ以外の場合、共通のキーはそれを含む最後の辞書の値を取ります。

!!! note "非推奨の注意"
    この関数は削除されます。代わりに[`TimeSeriesEcon.overlay`](@ref)を使用してください。重要な違いは、[`TimeSeriesEcon.overlay`](@ref)はキーが出現する場所で最初の引数からの値を保持するのに対し、`dictoverlay`は最後のものから保持することです。

