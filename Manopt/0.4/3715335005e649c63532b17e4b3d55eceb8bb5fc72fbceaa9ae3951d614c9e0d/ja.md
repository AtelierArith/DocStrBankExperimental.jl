```
DebugWarnIfLagrangeMultiplierIncreases <: DebugAction
```

バンドル法のラグランジュパラメータに基づく値 $-ξ$ が増加した場合に警告を表示します。

# コンストラクタ

```
DebugWarnIfLagrangeMultiplierIncreases(warn=:Once; tol=1e2)
```

警告を警告レベル（`:Once`）に初期化し、`1e2` のテストのための許容誤差を導入します。

`warn` レベルは、コストが増加したときに最初の1回だけ警告を表示するために `:Once` に設定することができ、毎回増加を報告するために `:Always` に設定することができ、警告を無効にするために `:No` に設定することができ、その場合この [`DebugAction`](@ref) は非アクティブになります。その他のシンボルはすべて `:Always` として扱われます。
