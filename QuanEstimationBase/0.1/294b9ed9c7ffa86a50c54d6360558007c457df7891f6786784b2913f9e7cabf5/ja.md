```
online(apt::Adapt_MZI; target::Symbol=:sharpness, output::String="phi")
```

MZIにおけるオンライン適応位相推定。

  * `apt`: x、p、およびrho0を含む適応MZI構造体。
  * `target`: 調整可能な位相を計算するためのターゲット関数を設定します。オプションは「sharpness」と「MI」です。
  * `output`: 出力変数を選択します。オプションは「phi」と「dphi」です。
