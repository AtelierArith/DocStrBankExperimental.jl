```
ode_default_options()
```

OrdinaryDiffEqの`solve`のデフォルトオプションを返します。`solve`に`ode_default_options()...`を渡すことで、最終時刻での解のみを返し、MPIが使用されている場合には**MPI対応**の誤差ベースのステップサイズ制御を有効にします。例えば、`solve(ode, alg; ode_default_options()...)`を使用します。
