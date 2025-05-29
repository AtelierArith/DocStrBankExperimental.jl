デバイアスされたモンドリアンランダムフォレストは、以下によって決定されます：

  * `lambda`: 非負のライフタイムパラメータ
  * `n_trees`: 森の中のモンドリアンツリーの数
  * `n_data`: データポイントの数
  * `n_evals`: 評価ポイントの数
  * `x_evals`: 評価ポイント
  * `debias_order`: 適用するデバイアスの順序
  * `significance_level`: 信頼区間のための有意水準
  * `X_data`: 共変量データ
  * `Y_data`: 応答データ
  * `debias_scaling`: ライフタイムスケーリング値
  * `debias_coeffs`: デバイアス係数
  * `trees`: 森で使用されるツリーのリスト
  * `mu_hat`: 推定回帰関数
  * `sigma2_hat`: 推定残差分散関数
  * `Sigma_hat`: 推定フォレスト分散関数
  * `confidence_band`: 回帰関数のための信頼帯
