```
set_optimizer_attributes(stochasticprogram::StochasticProgram, pairs::Pair...)
```

`attribute => value` ペアのリストまたはキーワード引数のコレクションを指定すると、各ペアに対して `set_optimizer_attribute(stochasticprogram, attribute, value)` を呼び出します。

関連情報: [`get_optimizer_attribute`](@ref)
