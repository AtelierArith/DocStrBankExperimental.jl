```
define_problem(; linear =["prices"], nonlinear = [""],
    cov = "all" or Vector{Tuple{String,String}},  # accept "all" to auto-pair nonlinear
    data, fixed_effects = [""],
    se_type = "bootstrap",
    cluster_var = "", constrained::Bool = false,
    drop_singletons = true, gmm_steps = 2, method = :cpu)
```

This function is used to construct a FRAC problem object. The key inputs are the data, the linear and nonlinear covariates, and the fixed effects,  all of which are specified as vectors of strings. The user can also specify the type of standard errors to be used, the cluster variable,  whether the model is constrained, and the number of GMM steps to be used. Presently, `method` is not used. 
