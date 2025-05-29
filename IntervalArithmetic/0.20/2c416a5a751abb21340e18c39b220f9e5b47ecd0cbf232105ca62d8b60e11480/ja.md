```
setformat(format=none; decorations=none, sigfigs=none)
```

`setformat` は、区間の表示方法を変更します。新しい `DisplayParameters` オブジェクトを返します。

`@format` マクロの方がユーザーフレンドリーであることに注意してください。

以下のオプションが利用可能です：

  * `format`: 区間出力形式

      * `:standard`: `[1, 2]`
      * `:full`: `Interval(1, 2)`
      * `:midpoint`: 1.5 ± 0.5
  * `sigfigs`: `standard` モードで表示する有効数字の数; デフォルトは 6
  * `decorations` (boolean): 装飾を表示するかどうか

例：

```
julia> setformat(:full, decorations=true)
Display parameters:
- format: full
- decorations: true
- significant figures: 6
```
