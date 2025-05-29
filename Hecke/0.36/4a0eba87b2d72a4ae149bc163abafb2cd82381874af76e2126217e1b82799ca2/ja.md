```
has_preimage_with_preimage(f::TorQuadModuleMap, b::TorQuadModuleElem)
                                  -> Bool, TorQuadModuleElem
```

アーベル群準同型 $f\colon T \to S$ が2つのトーション二次モジュールの間にあるとき、そして `b` が `S` の要素であるとき、`b` が `T` の像に含まれているかどうかを返します。もしそうであれば、関数は `f` による `b` の前像も返します。そうでない場合は、`T` の単位元を返します。
