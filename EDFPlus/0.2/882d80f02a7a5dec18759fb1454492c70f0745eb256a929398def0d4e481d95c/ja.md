```
epoch_iterator(edfh, epochsecs; channels, startsec, endsec, physical)
```

指定された期間のEEGエポックのイテレータを、開始時刻と終了時刻の間で作成します。

# 必須引数

  * edfh BEDFPlus構造体
  * epochsecs 各エポックの秒数の期間

# オプション引数

  * channels データのチャネル番号のリスト、デフォルトはすべての信号チャネル
  * startsec ファイルの開始時から0の位置、デフォルトはファイルの開始
  * endsec *ファイル*の開始からの秒数での終了位置、デフォルトはファイルの終了
  * physical データを物理単位に変換して返すかどうか、デフォルトはtrue
