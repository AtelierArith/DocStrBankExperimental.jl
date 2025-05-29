```julia
which_numa_node(arr::AbstractArray; ...) -> Int64
which_numa_node(arr::AbstractArray, i; kwargs...) -> Int64

```

与えられた配列がどのNUMAノードに割り当てられているかをクエリします（単一ノードに割り当てられていると仮定します）。

技術的には、単一の要素のアドレスのみがチェックされます（デフォルトでは最初の要素）。オプションの2番目の整数引数を使用して、この要素を指定できます。

オプションのキーワード引数 `variant` を使用して、NUMAノードを決定するために使用されるメソッドを切り替えることができます。有効なオプションは `:move_pages`（デフォルト）と `:get_mempolicy` です。

注意: 返されるNUMAノードIDはゼロから始まります！
