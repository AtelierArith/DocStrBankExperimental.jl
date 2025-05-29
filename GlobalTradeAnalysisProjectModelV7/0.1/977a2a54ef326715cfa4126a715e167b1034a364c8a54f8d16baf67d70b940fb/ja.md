```
    aggregate_data(; hData, hParameters, hSets, comMap, regMap, endMap)
```

提供されたマッピングベクターに基づいてデータ、パラメータ、およびセットを集約します。

### 引数:

  * `hData`: HARファイルに見られる名前を持つGTAPデータ（配列）の辞書
  * `hParameters`: HARファイルに見られる名前を持つGTAPパラメータ（配列）の辞書
  * `hSets`: HARファイルに見られる名前を持つGTAPセット（文字列のベクター）の辞書
  * `comMap`: セット`comm`の各要素に対して希望する集約名を提供するマッピングベクター（NamedVector）
  * `regMap`: セット`reg`の各要素に対して希望する集約名を提供するマッピングベクター（NamedVector）
  * `endMap`: セット`endw`の各要素に対して希望する集約名を提供するマッピングベクター（NamedVector）

### 戻り値:

集約データを含む要素hData、hParameters、hSetsを持つ名前付きタプル

### 例:

`julia (; hData, hParameters, hSets) = aggregate_data(hData=data, hParameters=parameters, hSets=sets, comMap=comMap, regMap=regMap, endMap=endMap)`
