```
multiplicative_group(A::Vector{AbsSimpleNumFieldElem}) -> FinGenAbGroup, Map
```

数体の乗法群の部分群を、`A`の要素によって生成される抽象アーベル群として返し、群の要素を数体の要素に、逆に数体の要素を群の要素にマッピングするマップを返します。
