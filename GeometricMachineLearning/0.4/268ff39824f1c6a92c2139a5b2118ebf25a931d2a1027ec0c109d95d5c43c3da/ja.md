```
DataLoader(data)
```

データセットに基づいてインスタンスを作成します。

これはトレーニングを便利にするために設計されています。

# `DataLoader`のフィールド

`DataLoader`構造体のフィールドは以下の通りです：

  * `input`: 軸 (i) システム次元、(ii) 時間ステップ数、(iii) パラメータ数を持つ入力データ。
  * `output`: 出力を含むテンソル（教師あり学習） - コンストラクタが1つのテンソルでのみ呼び出された場合（教師なし学習）、これは`Nothing`型である可能性があります。
  * `input_dim`: システムの*次元*、すなわち通常のニューラルネットワークが入力として受け取るもの。
  * `input_time_steps`: 全体の時系列の長さ（第2軸の長さ）。
  * `n_params`: データセットに存在するパラメータの数（第3軸の長さ）
  * `output_dim`: 出力テンソルの次元（第1軸）。`output`が`Nothing`型の場合、これも`Nothing`型です。
  * `output_time_steps`: 出力テンソルの第2軸のサイズ。`output`が`Nothing`型の場合、これも`Nothing`型です。

# 実装

`DataLoader`はさまざまな形式の入力で呼び出すことができますが、内部的には常に3つの軸を持つテンソルを保存します。

```jldoctest
using GeometricMachineLearning

data = [1 2 3; 4 5 6]
dl = DataLoader(data)
dl.input

# output

[ Info: You have provided a matrix as input. The axes will be interpreted as (i) system dimension and (ii) number of parameters.
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 4

[:, :, 2] =
 2
 5

[:, :, 3] =
 3
 6
```
