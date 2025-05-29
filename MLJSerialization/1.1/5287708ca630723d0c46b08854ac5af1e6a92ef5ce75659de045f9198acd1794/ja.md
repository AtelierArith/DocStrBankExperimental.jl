```
Save(filename="machine.jlso"; kwargs...)
```

イテレーション制御、例えば、`Save("run3/machine.jlso", compression=:gzip)` のように。

イテレートされている機械の現在の状態をディスクに保存します。提供された `filename` を使用し、番号で装飾します。例えば "run3/machine_42.jlso" のように。指定された `kwargs` は、モデル固有のシリアライザー（ほとんどのJuliaモデルに対してはJLSO）に渡されます。

「イテレートされている機械」とは何かについての詳細は、[`IteratedModel`](@ref) を参照してください。
