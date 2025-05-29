```
solve!(m::Model; [solver::Symbol])
```

与えられたモデルを解決し、指定されたソルバーに従って `m.solverdata` を更新します。ソルバーは `Symbol` として指定されます。デフォルトは `solve=:stackedtime` です。
