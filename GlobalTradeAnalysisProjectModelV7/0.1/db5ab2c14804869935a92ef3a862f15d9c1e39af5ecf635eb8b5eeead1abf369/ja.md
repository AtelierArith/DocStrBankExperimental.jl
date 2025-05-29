```
generate_starting_values(; hSets, hData, hParameters)
```

モデルに必要なすべての変数の初期値を生成します。これは通常、ユーザーによって呼び出されることはなく、初期モデルを生成する過程で呼び出されます。

### 引数:

  * `hSets`: セットの辞書
  * `hData`: データの辞書
  * `hParameters`: パラメータの辞書

### 戻り値:

6つの要素を持つ名前付きタプル: セット `sets`、パラメータ `parameters`、データ `data`、クローズ `fixed`、下限 `lower`、および上限 `upper`
