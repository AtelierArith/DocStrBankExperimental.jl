```
set!(solution, kwargs...)
```

解のフィールドを設定します。例えば、次のように使用します。

T0 = rand(4) S0(z) = exp(-z^2/10) set!(solution, T=T0, S=S0)

これにより、solution.T と solution.S が T0 と S0 に設定されます。
