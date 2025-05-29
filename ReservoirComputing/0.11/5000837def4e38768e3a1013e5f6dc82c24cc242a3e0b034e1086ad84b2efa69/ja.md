KnowledgeModel(prior_model, u0, tspan, datasize)

`Hybrid`バリエーションのエコーステートネットワーク（ESN）を構築します [^Pathak2018]。これは、ESNと知識ベースのモデル（`prior_model`）を統合しています。

# パラメータ

  * `prior_model`: ESNと統合するための知識ベースのモデル関数。
  * `u0`: モデルの初期条件。
  * `tspan`: モデルの操作期間を示すタプルとしての時間範囲。
  * `datasize`: 処理するデータのサイズ。

[^Pathak2018]: Jaideep Pathak et al. "Hybrid Forecasting of Chaotic Processes: Using Machine Learning in Conjunction with a Knowledge-Based Model" (2018).
