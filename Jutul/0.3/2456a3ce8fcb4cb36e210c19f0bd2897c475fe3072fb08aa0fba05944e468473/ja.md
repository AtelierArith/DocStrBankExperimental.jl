```
solve_adjoint_sensitivities(model, states, reports_or_timesteps, G; extra_timing = false, state0 = setup_state(model), forces = setup_forces(model), raw_output = false, kwarg...)
```

`model` パラメータの感度を目的関数 `G` に対して計算します。

目的関数は現在、すべての状態に対する合計として次の形式であると仮定されています: `obj = Σₙ G(model, state, dt_n, n, forces_for_step_n)`

随伴方程式を解きます: モデル方程式 F に対して、パラメータ p に関する勾配は     ∇ₚG = Σₙ (∂Fₙ / ∂p)ᵀ λₙ であり、ここで n ∈ [1, N] です。随伴方程式からのラグランジュ乗数 λₙ が与えられた場合、     (∂Fₙ / ∂xₙ)ᵀ λₙ = - (∂J / ∂xₙ)ᵀ - (∂Fₙ₊₁ / ∂xₙ)ᵀ λₙ₊₁ であり、最後の項はステップ n = N の場合に省略され、G は目的関数です。
