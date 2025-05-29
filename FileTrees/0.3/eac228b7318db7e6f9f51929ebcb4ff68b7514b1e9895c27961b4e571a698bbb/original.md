```
compute(tree::FileTree; cache=true)
```

Compute any lazy values (Thunks) in `tree` and return a new tree where the values refer to the computed values (maybe on remote processes). The tree still behaves as a Lazy tree. `exec` on it will fetch the values from remote processes.
