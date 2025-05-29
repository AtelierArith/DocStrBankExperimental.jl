```
alloc(h::HeapFunction, size::Integer; initialized::Bool=false) do size
    ptr = ...
end
```

メモリを割り当てるコードブロックをマークします。このブロックは、割り当てられたメモリへのポインタを返す必要があります。`initialized`引数は、メモリが初期化されているかどうかを示します。
