```
SimulationParamsType
```

非数値仿真パラメータ情報：

```
resultDir   ::String        結果フォルダのパス
ieT         ::Symbol        積分方程式のタイプ、EFIE、MFIE、CFIEなどを含む
meshfilename::String        メッシュファイル名
meshunit    ::Symbol        メッシュファイルの単位
SHOWIMAGE   ::Bool          フロントエンドに画像を表示するかどうか
discreteVar ::String        離散体未知量のタイプ、変位電流 `"D"` または等価電流 `"J"` をサポート
sbfT        ::Symbol        面基底関数のタイプ、現在は `:RWG` のみをサポート
vbfT        ::Symbol        体基底関数のタイプ、現在は `:SWG, :RBF, :PWC` をサポート
recordMem   ::Bool          メモリ情報を記録するかどうか
```
