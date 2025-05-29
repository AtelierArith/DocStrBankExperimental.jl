```
Broyden(;
    max_resets::Int = 100, linesearch = nothing, reset_tolerance = nothing,
    init_jacobian::Val = Val(:identity), autodiff = nothing, alpha = nothing,
    update_rule = Val(:good_broyden)
)
```

`Broyden`のメソッド[broyden1965class](@cite)の実装で、リセットとラインサーチを行います。

### キーワード引数

  * `max_resets`: 実行するリセットの最大数。デフォルトは`100`です。
  * `reset_tolerance`: リセットチェックのための許容誤差。デフォルトは`sqrt(eps(real(eltype(u))))`です。
  * `alpha`: `init_jacobian`が`Val(:identity)`に設定されている場合、初期ヤコビアンの逆行列は`(αI)⁻¹`に設定されます。デフォルトは`nothing`で、これは`α = max(norm(u), 1) / (2 * norm(fu))`を意味します。
  * `init_jacobian`: ヤコビアンを初期化するために使用する方法。デフォルトは`Val(:identity)`です。選択肢には以下が含まれます：

      * `Val(:identity)`: 単位行列。
      * `Val(:true_jacobian)`: 真のヤコビアン。これは微分可能な問題に対して良い選択です。
  * `update_rule`: ヤコビアンの更新ルール。選択肢は以下です：

      * `Val(:good_broyden)`: 良いブロイデンの更新ルール
      * `Val(:bad_broyden)`: 悪いブロイデンの更新ルール
      * `Val(:diagonal)`: ヤコビアンの対角成分のみを更新します。このアルゴリズムは特定の問題に対して有用かもしれませんが、機能するかどうかは問題に強く依存する可能性があります。
