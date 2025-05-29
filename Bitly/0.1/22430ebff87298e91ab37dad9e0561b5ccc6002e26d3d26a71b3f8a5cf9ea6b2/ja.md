`clicks(b::BitlyToken,link; summary=false,unit="day",units=-1,size=50)`

短縮リンク `link` のクリック情報を取得します。

`summary=true` は単一のカウントを提供し、それ以外の場合は時系列を返します。

`unit` は `"minute"`,`"hour"`,`"day"`,`"week"`,`"month"` のいずれかです。

`units` はデータを照会する時間単位の数を表す整数です。すべての利用可能な単位を返すには `-1` を渡します。

`size` は返されるアイテムの数量です。

`Dict` を返します。
