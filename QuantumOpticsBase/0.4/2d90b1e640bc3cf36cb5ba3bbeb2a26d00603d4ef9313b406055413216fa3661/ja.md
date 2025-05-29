```
set_time!(o::AbstractOperator, t::Number)
```

演算子の時計を設定します（[`AbstractTimeDependentOperator`](@ref）を参照）。`o`が他の演算子を含む場合（例えば、`o`が`LazyOperator`の場合）、それらに対して再帰的に`set_time!`を呼び出します。

`o`が時間依存でない場合、これは何もしません。
