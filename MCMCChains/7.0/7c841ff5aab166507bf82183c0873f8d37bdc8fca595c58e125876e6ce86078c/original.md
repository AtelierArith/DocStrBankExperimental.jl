```
describe(io, chains[;
         q = [0.025, 0.25, 0.5, 0.75, 0.975],
         etype = :bm,
         kwargs...])
```

Print chain metadata, summary statistics, and quantiles. Use `describe(chains)` for REPL output to `stdout`, or specify `io` for other streams (e.g., file output).
