```
next_signed_calkin_wilf(a::QQFieldElem)
```

符号付き有理数 $a$ を与えると、負の数が交互に挿入された Calkin-Wilf 数列の次の要素を返します。この数列は $0, 1, -1, 1/2, -1/2, 2, -2, 1/3, -1/3, \ldots$ で始まります。ゼロから始めると、すべての有理数を一度だけ生成しますが、最小の高さの順序ではありません。

# 例

```jldoctest
julia> next_signed_calkin_wilf(-ZZ(51)//(17))
1//4
```
