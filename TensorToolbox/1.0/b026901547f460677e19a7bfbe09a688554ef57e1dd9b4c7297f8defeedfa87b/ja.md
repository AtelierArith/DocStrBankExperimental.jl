hosvd1(X,Y; <keyword arguments>)

ttensor X と Y のアダマール積を ttensor として生成します。積を作成し、hosvd を呼び出します。関連情報: hosvd2, hosvd3, hosvd4。

## 引数:

  * `method` ∈ {"svd","lanczos","randsvd"}。SVD の手法。デフォルト: "randsvd"。
  * `reqrank::Vector`: 要求される多重線形ランク。オプション。
  * `eps_abs::Number/Vector`: eps_abs 未満の特異値（モード-n 行列化）の削除。オプション。
  * `eps_rel::Number/Vector`: eps*rel*sigma*1 未満の特異値（モード-n 行列化）の削除。オプション。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト p=10。
