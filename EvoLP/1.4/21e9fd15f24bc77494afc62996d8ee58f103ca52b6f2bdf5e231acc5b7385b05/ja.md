```
Logbook()
Logbook(S::LittleDict)
```

アルゴリズムの各イテレーションで使用するための統計のログです。ログブックは、統計名（文字列）を呼び出し可能なものにマッピングする `LittleDict` 順序付き辞書から構築され、*statname* $i$ は *callable* $i$ から計算できます。

結果として得られる `Logbook` には以下が含まれます：

  * `S::LittleDict`: 統計名と呼び出し可能なものの順序付き辞書
  * `records::AbstractVector`: 各フィールドが統計である NamedTuples のベクター。

引数が渡されない場合、ログブックは最小値、平均、中央値、最大値、標準偏差などの一般的な統計のセットで構築されます。
