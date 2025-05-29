```
FortranString{CharType}
```

FORTRAN `CHARACTER*N` 文字列をエミュレートするためのデータ型。

この型は、`CharType` 型の要素を持つ `Vector` のラッパーです。限られた文字列エミュレーションのためにいくつかの関数とブロードキャスティングが追加されています。

代入はブロードキャスティングを介して行うべきです：

```jldoctest
julia> s = F8"abc"; s .= "AB" * F"CD"; s
F8"ABC"

julia> s = F"abc"; s[2:end] .= "ABC"; s
F"aAB"
```

要素ごとの代入もサポートされていますが、FORTRAN とは似ていません。要素の比較

```jldoctest
julia> s = F8"abc"; s[1:1] == 'a'
true

julia> s = F8"abc"; (s[1:1] == 'a', s[2:2] == "b")
(true, true)
```

引用のために `@F_str` も参照してください。
