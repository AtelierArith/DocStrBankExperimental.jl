```
setup_parameter_optimization(model, state0, param, dt, forces, G, opt_cfg = optimization_config(model, param);
                                                        grad_type = :adjoint,
                                                        config = nothing,
                                                        print = 1,
                                                        copy_case = true,
                                                        param_obj = false,
                                                        kwarg...)
```

Set up function handles for optimizing the case defined by the inputs to `simulate` together with a per-timestep objective function `G`. The objective should be on the form of sum over all steps, where each element of the sum is evaluated by `model, state, dt, step_no, forces`.

Generally calling either of the functions will mutate the data Dict. The options are: F*o(x) -> evaluate objective dF*o(dFdx, x) -> evaluate gradient of objective, mutating dFdx (may trigger evaluation of F*o) F*and_dF(F, dFdx, x) -> evaluate F and/or dF. Value of nothing will mean that the corresponding entry is skipped.
