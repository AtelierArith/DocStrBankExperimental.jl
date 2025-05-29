`T`型のオブジェクトの配列をランレングス圧縮を使用してエンコードしたもの。

これは配列のように機能しますが、配列が長く、同じ要素の長い繰り返し（「ラン」）で構成されている場合に非常に効率的になるように設計されています。各ランの長さは`N`型を使用して保持されます。この型は、ランの最大長に基づいて選択する必要があります。

`RunLengthArray`が作成されると、新しい要素は`push!`（1つの要素を追加）または`append!`（要素のシーケンスを追加）を使用してのみ、その末尾に追加できます。

```julia
arr = RunLengthArray{Int, Int8}(Int8[3, 3, 3, 7, 7, 7, 7, 7, 7, 4])

longarr = collect(arr)

@assert length(arr) == 10
@assert sum(arr) == 30
@assert arr[1] == 3
@assert arr[2] == 3

println("$(sizeof(arr))")  # Prints 16 (bytes)
println("$(sizeof(longarr))")  # Prints 56 (bytes)
```
