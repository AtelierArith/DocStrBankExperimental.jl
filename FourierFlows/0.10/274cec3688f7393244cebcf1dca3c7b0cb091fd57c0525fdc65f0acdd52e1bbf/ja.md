```
stepforward!(prob::Problem, diags, nsteps::Int)
```

`prob`を`nsteps`だけ前進させ、途中で`diags`を増加させます。`diags`は単一の`Diagnostic`または`Diagnostic`の`Vector`である可能性があります。
