```
push!!(vi::VarInfo, vn::VarName, r, dist::Distribution)
```

新しいランダム変数 `vn` を、分布 `dist` からサンプリングされた値 `r` と共に `VarInfo` `vi` にプッシュします。意味がある場合はミューテーションを行います。
