```
set_state!(ds::DynamicalSystem, value::Real, i) → u
```

`ds`の`i`番目の変数を`value`に設定します。インデックス`i`は整数またはModelingToolkit.jlモデルを参照するシステムのためのシンボリックなインデックスであることができます。例えば：

```julia
i = :x # または `1` または `only(@variables(x))`
set_state!(ds, 0.5, i)
```

**警告:** この関数は、ポアンカレ/ストロボスコピック/投影ダイナミカルシステムなどの導関数ダイナミカルシステムでは使用しないでください。配列を操作してそれを`set_state!`に渡すために、以下のメソッドを使用してください。

```
set_state!(u::AbstractArray, value, index, ds::DynamicalSystem)
```

与えられた状態`u`を修正し、`ds`はそのままにします。
