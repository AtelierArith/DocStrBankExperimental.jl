`SimplifiedString(∇V, integrate!, reparameterize!, dist, Δt)` - 簡略化された文字列メソッドのデータ構造を設定します

### フィールド

  * `∇V`   - ポテンシャルの勾配
  * `integrate!` - ẋ = - ∇V(x) のための積分器
  * `reparameterize!` - 再パラメータ化の選択
  * `dist` - 再パラメータ化と収束テストに使用される距離関数
  * `pin` - 文字列の端点を固定するためのブール値
  * `Δt`    - 積分器の時間ステップ
