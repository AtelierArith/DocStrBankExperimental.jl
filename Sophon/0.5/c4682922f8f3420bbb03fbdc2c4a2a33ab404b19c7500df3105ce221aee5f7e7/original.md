```
 discretize(pde_system::PDESystem, pinn::PINN, sampler::PINNSampler,
                strategy::AbstractTrainingAlg; derivative=finitediff,
                additional_loss)
```

Convert the PDESystem into an `OptimizationProblem`. You will have access to each loss function `Sophon.residual_function_1`, `Sophon.residual_function_2`... after calling this function.
