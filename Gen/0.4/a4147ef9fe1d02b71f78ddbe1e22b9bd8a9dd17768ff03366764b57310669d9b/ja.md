```
struct DynamicSelection <: HierarchicalSelection .. end
```

階層的で可変な、任意のアドレスを持つ選択。

以下のメソッドで変更可能です：

```
Base.push!(selection::DynamicSelection, addr)
```

アドレスとそのすべてのサブアドレスを選択に追加します。

例：

```julia
selection = select()
@assert !(:x in selection)
push!(selection, :x)
@assert :x in selection
```

```
set_subselection!(selection::DynamicSelection, addr, other::Selection)
```

指定されたアドレスと、そのサブアドレスの選択状態を `other` で定義されたものに変更します。

例：

```julia
selection = select(:x)
@assert :x in selection
subselection = select(:y)
set_subselection!(selection, :x, subselection)
@assert (:x => :y) in selection
@assert !(:x in selection)
```

`set_subselection!` は `other` のデータをコピーしないため、`addr` の下のアドレスに対する後の `set_subselection!` の呼び出しによって `other` が変更される可能性があります。
