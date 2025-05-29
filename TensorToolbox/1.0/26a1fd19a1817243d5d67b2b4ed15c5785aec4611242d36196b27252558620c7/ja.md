hosvd3(X,Y; <キーワード引数>)

ttensor XとYのアダマール積をttensorとして返します。構造を利用しており、(X ∗ Y)ₙ(X ∗ Y)ₙᵀ行列で動作します。関連情報: hosvd1, hosvd2, hosvd4。

## 引数:

  * `method` ∈ {"lanczos","randsvd"} SVDのための構造を利用する方法。デフォルト: "lanczos"。
  * `reqrank::Vector`: 要求される多重線形ランク。オプション。
  * `variant` ∈ {'A','B'} 積のバリアント (X ∗ Y)ₙ(X ∗ Y)ₙᵀ。デフォルト: 'B'。
  * `eps_abs::Number/Vector`: eps_abs未満の特異値（モード-nの行列化）を削除します。オプション。
  * `eps_rel::Number/Vector`: eps*rel*sigma*1未満の特異値（モード-nの行列化）を削除します。オプション。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト p=10。
