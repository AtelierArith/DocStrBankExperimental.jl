```
Element(name, symbol, weight)
```

フィールドを持つ型:

  * `.name`:  要素の名前 (`::String`)
  * `.symbol`:  要素の記号 (`::String`)
  * `.weight`:  相対原子質量 - 原子量 (`::Float64`)

型 `Element` は関数 [`castElement`](@ref) を使って作成するのが最適です。
