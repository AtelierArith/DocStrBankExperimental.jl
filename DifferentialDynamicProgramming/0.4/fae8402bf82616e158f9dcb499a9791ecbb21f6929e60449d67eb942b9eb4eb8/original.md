```
`x, u, traj_new, Vx, Vxx, cost, trace = iLQGkl(dynamics,costfun,derivs, x0, traj_prev, model;
    constrain_per_step = false,
    kl_step            = 0,
    lims               = [],                    # Control signal limits ::Matrix ∈ R(m,2)
    tol_fun            = 1e-7,
    tol_grad           = 1e-4,
    max_iter           = 50,
    print_head         = 10,                    # Print headers this often
    print_period       = 1,                     # Print this often
    reduce_ratio_min   = 0,                     # Not used ATM
    diff_fun           = -,
    verbosity          = 2,                     # ∈ (0,3)
    plot_fun           = x->0,                  # Not used
    cost               = [],                    # Supply if pre-rolled trajectory supplied
    ηbracket           = [1e-8,1,1e16],         # dual variable bracket [min_η, η, max_η]
    del0               = 0.0001,                # Start of dual variable increase
    gd_alpha           = 0.01                   # Step size in GD (ADAMOptimizer) when constrain_per_step is true
    )`
```

Solves the iLQG problem with constraints on control signals `lims` and bound on the KL-divergence `kl_step` from the old trajectory distribution `traj_prev::GaussianPolicy`.

To solve the maximum entropy problem, use controller `controller(xi,i)  = u[:,i] + K[:,:,i]*(xi-x[:,i]) + chol(Σ)*randn(m)` where `K` comes from `traj_new`. Note that multiplying the cost by a constant changes the relative weight between the cost term and the entropy term, i.e., higher cost produces less noise through chol(Σ) since (Σ = Qᵤᵤ⁻¹).
