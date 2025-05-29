```
set_suboptimizer_attributes(stochasticprogram::StochasticProgram, pairs::Pair...)
```

`attribute => value` ペアのリストまたはキーワード引数のコレクションを指定すると、各ペアに対して `set_suboptimizer_attribute(stochasticprogram, attribute, value)` を呼び出します。
