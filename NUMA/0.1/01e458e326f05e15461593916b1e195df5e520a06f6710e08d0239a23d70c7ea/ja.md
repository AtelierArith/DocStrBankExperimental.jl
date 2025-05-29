```julia
which_numa_node(ptr::Ptr{T}; variant) -> Int64

```

指定されたメモリアドレス（ポインタ）に関連付けられたページがどのNUMAノードにあるかをクエリします。

オプションのキーワード引数`variant`を使用して、NUMAノードを決定するために使用されるメソッドを切り替えることができます。有効なオプションは`:move_pages`（デフォルト）と`:get_mempolicy`です。

注意: 返されるNUMAノードIDはゼロから始まります！
