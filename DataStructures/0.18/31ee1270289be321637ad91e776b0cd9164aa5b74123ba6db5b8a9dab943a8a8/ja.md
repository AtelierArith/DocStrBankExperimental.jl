```
 nlargest(acc::Accumulator, [n])
```

最も一般的な要素の `n` 個をカウントと共にソートされたベクターとして返します。`n` が省略された場合、完全なソートされたコレクションが返されます。

これはPythonの `Counter.most_common` 関数に対応します。

例

```
julia> nlargest(counter("abbbccddddda"))

4-element Array{Pair{Char,Int64},1}:
 'd'=>5
 'b'=>3
 'c'=>2
 'a'=>2


julia> nlargest(counter("abbbccddddda"),2)

2-element Array{Pair{Char,Int64},1}:
 'd'=>5
 'b'=>3

```
