```
 discretize(pde_system::PDESystem, pinn::PINN, sampler::PINNSampler,
                strategy::AbstractTrainingAlg; derivative=finitediff,
                additional_loss)
```

PDESystemを`OptimizationProblem`に変換します。この関数を呼び出した後、各損失関数`Sophon.residual_function_1`、`Sophon.residual_function_2`...にアクセスできます。
