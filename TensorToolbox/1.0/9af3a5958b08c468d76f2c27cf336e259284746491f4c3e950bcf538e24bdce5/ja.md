hosvd4(X,Y; <keyword arguments>)

ttensor X と Y のアダマール積を ttensor として返します。 (X ∗ Y)ₙ の範囲を見つけるためにランダム化されたランク1アルゴリズムを使用します。 reqrank が定義されている場合、更新されたコアテンソルに対して追加の hosvd を呼び出します。 参照: hosvd1, hosvd2, hosvd3。

## 引数:

  * `method` ∈ {"svd","lanczos","randsvd"} SVD のためのメソッド。 デフォルト: "svd"。
  * `reqrank::Vector`: 要求された多重線形ランク。 オプション。
  * `eps_abs::Number/Vector`: eps_abs 未満の特異値（モード-n マトリクス化）のドロップ。 オプション。
  * `eps_rel::Number/Vector`: eps*rel*sigma*1 未満の特異値（モード-n マトリクス化）のドロップ。 オプション。
  * `p::Integer`: オーバーサンプリングパラメータ。 デフォルト p=10。
