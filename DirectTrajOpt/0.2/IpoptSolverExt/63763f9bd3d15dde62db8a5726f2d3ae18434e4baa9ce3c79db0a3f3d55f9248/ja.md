solve!(prob::DirectTrajOptProblem;         init*traj=nothing,         save*path=nothing,         max*iter=prob.ipopt*options.max*iter,         linear*solver=prob.ipopt*options.linear*solver,         print*level=prob.ipopt*options.print*level,         remove*slack*variables=false,         callback=nothing         # state*type=:unitary,         # print_fidelity=false,     )

```
最適化ソルバーを呼び出して、パラメータとコールバックを使用して量子制御問題を解決します。
```

# 引数

  * `prob::DirectTrajOptProblem`: 解決すべき量子制御問題。
  * `init_traj::NamedTrajectory`: 制御軌道の初期推測。提供されない場合は、ランダムな推測が生成されます。
  * `save_path::String`: 最適化後に問題を保存するパス。
  * `max_iter::Int`: 最適化ソルバーの最大反復回数。
  * `linear_solver::String`: 最適化ソルバーで使用する線形ソルバー（例："mumps"、"paradiso"など）。
  * `print_level::Int`: ソルバーの冗長性レベル。
  * `callback::Function`: 最適化ステップ中に呼び出すコールバック関数。
