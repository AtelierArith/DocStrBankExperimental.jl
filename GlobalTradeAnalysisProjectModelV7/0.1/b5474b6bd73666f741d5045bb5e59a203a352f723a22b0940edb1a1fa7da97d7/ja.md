```
generate_initial_model(; hSets, hData, hParameters)
```

データ、パラメータ、およびセットに基づいて初期モデルコンテナを生成します。

### 引数:

  * `hSet`: セットの辞書
  * `hData`: データの辞書
  * `hParameters`: パラメータの辞書

## 戻り値:

以下の要素を持つモデルコンテナ:

  * `model`: 空のIpoptモデル
  * `data`: データの辞書（モデル内の変数）
  * `parameters`: パラメータ値の辞書
  * `sets`: セットの辞書
  * `fixed`: モデルの閉包を定義するBoolean配列の辞書（外生/固定変数）
  * `lower`: モデル変数の下限の辞書
  * `upper`: モデル変数の上限の辞書

### 例:

$$
julia generate_initial_model(; hSets, hData, hParameters)
$$
