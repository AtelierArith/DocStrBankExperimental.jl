```
GI = fillnodata(data::String; nodata=nothing, kwargs...) -> GMTgrid or GMTimage
```

選択したラスタ領域をエッジからの補間によって埋めます。

### パラメータ

  * `data`: 入力データ。`gmtread`で読み取ることができるグリッドまたは画像のファイル名。
  * `nodata`: 領域を埋めるために使用されるノーデータ値。それ以外の場合は、`indata`の`nodata`属性を使用します（存在する場合）。どちらも設定されていない場合はNaNを使用します。
  * `kwargs`:

      * band: バンド番号。デフォルトは`indata`の最初のレイヤー。
      * maxdist: 補間するために値を見つけるためにすべての方向で検索する最大セル数。デフォルトはすべてを埋めます。
      * nsmooth: 実行する3x3スムージングフィルターのパスの数（0以上）。

### 戻り値

`band`のノーデータ値が補間によって埋められたGMTgridまたはGMTimageオブジェクト。
