```
DebugWarnIfCostNotFinite <: DebugAction
```

AbstractManoptSolverState内のフィールド（値または配列）が有限でない値（例えば`Inf`や`Nan`）を持つかどうかを確認するためのデバッグです。

# コンストラクタ

```
DebugWarnIfCostNotFinite(field::Symbol, warn=:Once)
```

警告を`：Once`に初期化します。

これは、コストがNanのときに最初の1回だけ警告するために`:Once`に設定できます。また、警告を無効にするために`:No`に設定することもできますが、これによりこのアクションも無意味になります。他のすべてのシンボルは`:Always:`のように扱われます。
