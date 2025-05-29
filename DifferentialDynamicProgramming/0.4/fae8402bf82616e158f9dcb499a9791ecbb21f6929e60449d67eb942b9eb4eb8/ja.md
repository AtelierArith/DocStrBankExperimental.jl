```
`x, u, traj_new, Vx, Vxx, cost, trace = iLQGkl(dynamics,costfun,derivs, x0, traj_prev, model;
    constrain_per_step = false,
    kl_step            = 0,
    lims               = [],                    # 制御信号の制限 ::Matrix ∈ R(m,2)
    tol_fun            = 1e-7,
    tol_grad           = 1e-4,
    max_iter           = 50,
    print_head         = 10,                    # この頻度でヘッダーを印刷
    print_period       = 1,                     # この頻度で印刷
    reduce_ratio_min   = 0,                     # 現在は使用されていません
    diff_fun           = -,
    verbosity          = 2,                     # ∈ (0,3)
    plot_fun           = x->0,                  # 使用されていません
    cost               = [],                    # 事前にロールされた軌道が供給される場合に供給
    ηbracket           = [1e-8,1,1e16],         # 双対変数の範囲 [min_η, η, max_η]
    del0               = 0.0001,                # 双対変数の増加の開始
    gd_alpha           = 0.01                   # constrain_per_step が true のときの GD (ADAMOptimizer) のステップサイズ
    )`
```

制御信号 `lims` に制約を設け、古い軌道分布 `traj_prev::GaussianPolicy` からの KL-ダイバージェンス `kl_step` に制約を設けた iLQG 問題を解決します。

最大エントロピー問題を解決するには、`controller(xi,i)  = u[:,i] + K[:,:,i]*(xi-x[:,i]) + chol(Σ)*randn(m)` を使用します。ここで `K` は `traj_new` から得られます。コストに定数を掛けると、コスト項とエントロピー項の相対的な重みが変わることに注意してください。つまり、コストが高いほど chol(Σ) を通じてノイズが少なくなります（Σ = Qᵤᵤ⁻¹）。
