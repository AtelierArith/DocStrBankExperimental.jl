```
initstate(domain::Domain, problem::Problem)
initstate(domain::Domain, objtypes[, fluents])
```

与えられた計画 `domain` と `problem` の初期状態を構築するか、`domain`、オブジェクトのタイプへのマップ (`objtypes`)、およびオプションの `fluents` リストから初期状態を構築します。

フルエントは、PDDL 問題における初期フルエントを表す `Term` のリストとして提供されるか、フルエント名からフルエント値へのマップとして提供されることがあります。
