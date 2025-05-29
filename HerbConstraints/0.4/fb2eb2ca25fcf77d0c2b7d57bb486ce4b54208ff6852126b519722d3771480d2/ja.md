```
isfeasible(solver::GenericSolver)
```

不整合が検出されていない場合にtrueを返します。いくつかの方法で使用されます：

  * イテレータは不整合をチェックして不整合な状態を破棄する必要があります
  * 不整合の可能性がある任意のツリー操作の後（例：`remove_below!`、`remove_above!`、`remove!`）
  * `fix_point!`は不整合をチェックしてスケジュールをクリアし、戻る必要があります
  * 一部の`GenericSolver`関数はデバッグ目的で実行可能な状態を主張します `@assert isfeasible(solver)`
  * 一部の`GenericSolver`関数には、不整合な状態で関数をスキップするガードがあります：`if !isfeasible(solver) return end`
