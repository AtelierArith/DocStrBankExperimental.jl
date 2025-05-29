hosvd2(X,Y; <keyword arguments>)

ttensor X と Y のアダマール積を ttensor として返します。構造から因子行列を直交化し、更新されたコアテンソルに対して hosvd を呼び出します。関連情報: hosvd1, hosvd3, hosvd4。

## 引数:

  * `method` ∈ {"svd","lanczos","randsvd"} SVD の方法。デフォルト: "randsvd"。
  * `reqrank::Vector`: 要求される多重線形ランク。オプション。
  * `eps_abs::Number/Vector`: eps_abs 未満の特異値（モード-n 行列化）の削除。オプション。
  * `eps_rel::Number/Vector`: eps*rel*sigma*1 未満の特異値（モード-n 行列化）の削除。オプション。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト p=10。
