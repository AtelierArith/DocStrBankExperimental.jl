```
sub(s::Vector{FinGenAbGroupElem}) -> FinGenAbGroup, FinGenAbGroupHom
```

非空の配列 `s` がアーベル群 $G$ の要素を含むと仮定すると、この関数は `s` の要素によって生成される $G$ の部分群 $H$ と、注入 $\iota : H \to G$ を返します。
