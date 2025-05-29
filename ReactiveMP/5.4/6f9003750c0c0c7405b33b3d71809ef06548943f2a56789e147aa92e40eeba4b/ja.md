`compile(model::FlowModel, params::Vector)` は、パラメータのベクトル `params` を使用してモデル `model` を初期化することができます。

入力引数

  * `model::FlowModel` - レイヤー/フローの次元が初期化されたモデルですが、パラメータは設定されていません。
  * `params::Vector`   - モデルをコンパイルするためのパラメータのベクトルです。

戻り値

  * `::CompiledFlowModel` - パラメータが設定されたコンパイル済みモデルで、データ処理に使用できます。
