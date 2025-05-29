```
gmtconnect(cmd0::String="", arg1=nothing, kwargs...)
```

個々の線の端点が許容範囲内で一致する場合に接続します

## パラメータ

  * **C** | **closed** :: [Type => Str | []]        `Arg = [closed]`

    すべての閉じたポリゴンを closed [gmtgmtconnect_closed.txt] に書き込み、他のすべてのセグメントはそのまま返します。gmtconnectionは行われません。
  * **D** | **dump** :: [Type => Str | []]   `Arg = [template]`

    複数のセグメントデータの場合、各セグメントを別々の出力ファイルにダンプします。
  * **L** | **links** | **linkfile** :: [Type => Str | []]      `Arg = [linkfile]`

    指定されたファイル [gmtgmtconnect_link.txt] にリンク情報を書き込みます。
  * **Q** | **list** | **listfile** :: [Type => Str | []]      `Arg =  [listfile]`

    **D** と共に使用して、個々の出力ファイルの名前を含むリストファイルを書き込みます。
  * **T** | **tolerance** :: [Type => Str | List]    `Arg = [cutoff[unit][/nn_dist]]`

    データ座標単位での分離許容範囲を指定します [0]; 距離単位を追加します。2つの線の端点がこのカットオフよりも近い場合、それらは結合されます。

完全なドキュメントを見るには、次のように入力してください: $@? gmtconnect$
