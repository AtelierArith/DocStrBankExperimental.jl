`arrangements(mset[,k])`, `narrangements(mset[,k])`

`arrangements` は、マルチセット `mset` の配置を返します（必ずしもソートされていない、可能な繰り返しを含むコレクション）。第二引数 `k` が与えられた場合、`k` 要素の配置を返します。`narrangements` は（より速く）配置の数を返します。

`k` 要素を持つ `mset` の *配置* は、任意の順序で取られた長さ `k` の部分列であり、`Vector` として表されます。`k==length(mset)` の場合、それはまた置換と呼ばれます。

マルチセットの配置の例として、ゲームのスクラブルを考えてみてください。単語「settle」の6文字を持っていて、2文字の単語を作らなければならないとします。すると、可能性は次のように与えられます。

```julia-repl
julia> narrangements("settle",2)
14
```

一方、すべての可能な単語（空の単語を含む）は次の通りです：

```julia-repl
julia> narrangements("settle")
523
```

`arrangements` によって返される結果はソートされており（`mset` の要素はソート可能でなければなりません）、この例では可能性が辞書に現れるのと同じ順序でリストされていることを意味します。以下は2文字の単語です：

```julia-repl
julia> String.(arrangements("settle",2))
14-element Vector{String}:
 "ee"
 "el"
 "es"
 "et"
 "le"
 "ls"
 "lt"
 "se"
 "sl"
 "st"
 "te"
 "tl"
 "ts"
 "tt"
```
