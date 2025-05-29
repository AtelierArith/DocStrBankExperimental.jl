```
DebugWarnIfFieldNotFinite <: DebugAction
```

オプションからのフィールドが有限でない場合、例えば `Inf` や `Nan` のときに警告を表示するデバッグです。

# コンストラクタ

```
DebugWarnIfFieldNotFinite(field::Symbol, warn=:Once)
```

警告を `:Once` に設定して初期化します。

これは、コストが最初に `Nan` のときだけ警告するように `:Once` に設定できます。また、警告を無効にするために `:No` に設定することもできますが、これによりこのアクションも無意味になります。他のすべてのシンボルは `:Always` のように扱われます。

# 例

```
DebugWaranIfFieldNotFinite(:Gradient)
```

勾配が `Nan` または `Inf` にならないかを追跡する [`DebugAction`] を作成します。
