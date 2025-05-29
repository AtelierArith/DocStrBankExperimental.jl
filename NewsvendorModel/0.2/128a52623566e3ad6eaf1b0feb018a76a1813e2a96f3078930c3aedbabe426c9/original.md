```
solve(nvm::NVModel [; rounded = true])
```

Compute the stocking quantity `q_opt(nvm)` that maximizes the expected profit  as well as further the metrics when using it. The optimal quantity is rounded up to the next integer by default. To get the  exact real number, set the keyword arguement `rounded = false`.
