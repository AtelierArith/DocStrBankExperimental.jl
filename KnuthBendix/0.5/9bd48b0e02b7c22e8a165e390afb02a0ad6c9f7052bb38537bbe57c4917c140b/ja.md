```
isconfluent(rws::RewritingSystem)
```

書き換えシステムが同値であるかどうかを確認します。

!!! note
    [`check_confluence`](@ref) は **簡約化された** 書き換えシステムに対して比較的安価であるため、`isconfluent` は自動的にシステムを簡約化しようとはせず、`false` を返します。確定的な答えを得るには、`isconfluent` を呼び出す前に書き換えシステムを [`reduce!`](@ref) する必要があります。

