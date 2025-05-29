```
levels(x::CategoricalArray; skipmissing=true)
levels(x::CategoricalValue)
```

カテゴリカル配列または値 `x` のレベルを返します。これには、データに実際には現れないレベルが含まれる場合があります（[`droplevels!`](@ref）を参照）。`missing` は、データに現れ、`skipmissing=false` が渡された場合にのみ含まれます。

返されるベクターは `x` の内部フィールドであり、変更してはいけません。変更すると、それが破損します。
