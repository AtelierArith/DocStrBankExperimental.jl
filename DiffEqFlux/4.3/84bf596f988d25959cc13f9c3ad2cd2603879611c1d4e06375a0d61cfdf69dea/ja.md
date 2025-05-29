```
multiple_shoot(p, ode_data, tsteps, prob, loss_function,
    [continuity_loss = _default_continuity_loss], solver, group_size;
    continuity_term = 100, kwargs...)
```

ODEデータに対して「直接的なマルチプルシューティング」を試みた後、各グループ（小さな区間）からの予測の配列とともに合計損失を返します。直接的なマルチプルシューティングでは、ニューラルネットワークが区間を小さな区間に分割し、それらを別々に解決します。デフォルトの連続性項は100であり、これは異なる2つのグループの非連続性から生じる損失が100倍されることを意味します。

引数:

  * `p`: 学習されるニューラルネットワークのパラメータ。
  * `ode_data`: モデリングされる元のデータ。
  * `tsteps`: ode_dataが計算されたタイムステップ。
  * `prob`: ニューラルネットワークが解決しようとするODE問題。
  * `loss_function`: 損失を計算するための任意の関数。
  * `continuity_loss`: グループ$k$の状態$\hat{u}_{end}$とグループ$k+1$の$u_{0}$を入力として受け取り、それらの間の予測の連続性損失を計算する関数。カスタムの`continuity_loss`が指定されていない場合、`sum(abs, û_end - u_0)`が使用されます。
  * `solver`: ODEソルバーアルゴリズム。
  * `group_size`: ode_dataを等しいサイズに分割した後に達成されるグループサイズ。
  * `continuity_term`: 異なるグループ間での予測の連続性を確保するための重み項。
  * `kwargs`: ODEソルバーにスプラットされる追加の引数。詳細については、[ローカル感度分析](https://docs.sciml.ai/SciMLSensitivity/stable/)および[一般的なソルバー引数](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)のドキュメントを参照してください。

!!! note
    パラメータ「continuity_term」は、任意のグループの最後のポイントが次のグループの最初のポイントと一致しない場合に大きなペナルティを課すために、比較的大きな数であるべきです。

