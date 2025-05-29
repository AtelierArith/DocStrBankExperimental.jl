```
reservoir_linsolve(model, precond = :cpr; <keyword arguments>)
```

[`setup_reservoir_model`](@ref)からの貯水池モデルのための反復線形ソルバーを設定します。

# 引数

  * `model`: 線形ソルバーのために方程式を線形化する貯水池モデル
  * `precond=:cpr`: 使用する前処理器のタイプ: :cpr (制約圧力残差) または :ilu0 (ブロック不完全LU) (:directの場合は効果なし)
  * `v=0`: 冗長性 (大量の出力を引き起こす可能性があります)
  * `solver=:bicgstab`: Krylov.jlソルバーのシンボル (通常は :gmres または :bicgstab)
  * `update_interval=:once`: CPR AMG階層が再構築される頻度 (:once, :iteration, :ministep, :step)
  * `update_interval_partial=:iteration`: CPRで圧力システムが更新される頻度
  * `max_coarse`: AMGを使用する場合の粗いレベルの最大サイズ
  * `cpr_type=nothing`: CPRのタイプ (`:true_impes`, `:quasi_impes` または自動のための `nothing`)
  * `partial_update=true`: AMG更新の外でCPR前処理器の部分更新を実行する (上記参照)
  * `rtol=1e-3`: 線形ソルバーの相対許容誤差
  * `max_iterations=100`: 線形ソルバーの反復回数の制限

追加のキーワードは線形ソルバーコンストラクタに渡されます。
