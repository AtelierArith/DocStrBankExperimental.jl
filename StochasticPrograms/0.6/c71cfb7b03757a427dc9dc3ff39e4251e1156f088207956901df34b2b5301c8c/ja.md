```
supports_structure(optimizer::StochasticProgramOptimizerType, structure::AbstractStochasticStructure)
```

`optimizer`が確率的`structure`をサポートしているかどうかを示す`Bool`を返します。つまり、`load_structure!(optimizer, structure)`は`UnsupportedStructure`をスローしません。
