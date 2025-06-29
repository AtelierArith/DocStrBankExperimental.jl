```
MB_timestep!(model::Model, glacier::G, step::F, t; batch_id::Union{Nothing, I} = nothing) where {I <: Integer, F <: AbstractFloat, G <: AbstractGlacier}
```

与えられた氷河モデルの質量収支タイムステップをシミュレートします。

# 引数

  * `model::Model`: 氷流と質量収支情報を含む氷河モデル。
  * `glacier::G`: 気候とDEMデータを含む氷河オブジェクト。
  * `step::F`: タイムステップの期間。
  * `t`: 現在の時間。
  * `batch_id::Union{Nothing, I}`: 逆微分を使用したシミュレーションのためのオプションのバッチ識別子。デフォルトは `nothing`。

# 説明

この関数は以下のステップを実行します：

1. 前のタイムステップから現在の時間までの期間を計算します。
2. 指定された期間の累積気候データを取得します。
3. 氷河のDEMに基づいて気候データセットを2Dグリッドにダウンスケールします。
4. 氷河の質量収支を計算し、モデルの氷流質量収支を更新します。

`batch_id` が提供されている場合、関数は指定されたバッチの質量収支を更新します。そうでない場合は、モデル全体の質量収支を更新します。
