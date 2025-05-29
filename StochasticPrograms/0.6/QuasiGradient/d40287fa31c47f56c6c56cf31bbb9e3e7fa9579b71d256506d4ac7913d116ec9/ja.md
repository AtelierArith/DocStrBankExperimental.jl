```
set_prox_attributes(stochasticprogram::StochasticProgram, pairs::Pair...)
```

`attribute => value` ペアのリストまたはキーワード引数のコレクションが与えられた場合、各ペアに対して `set_prox_attribute(stochasticprogram, attribute, value)` を呼び出します。
