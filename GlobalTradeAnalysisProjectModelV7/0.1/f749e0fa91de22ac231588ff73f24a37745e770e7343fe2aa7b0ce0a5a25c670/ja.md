```
get_sample_data()
```

公開されているGTAPデータベースのバージョン9から小さなサンプルデータセットを返します。

### 引数:

  * なし

### 戻り値:

名前付きタプルで、

  * `hData`: サンプル集約データを含む辞書
  * `hParamters`: サンプル集約パラメータを含む辞書
  * `hSets`: サンプル集約セットを含む辞書

### 例:

`julia (; hData, hParameters, hSets) = get_sample_data()`
