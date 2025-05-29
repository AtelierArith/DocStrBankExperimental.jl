```
DebugEntry <: DebugAction
```

イテレーション中に特定のフィールドエントリを印刷します。ここで、エントリを印刷する方法を指定できる `format` があります。

# 追加フィールド

  * `field`: [`AbstractManoptSolverState`](@ref) 内でアクセスできるシンボル

# コンストラクタ

```
DebugEntry(f; prefix="$f:", format = "$prefix %s", io=stdout)
```
