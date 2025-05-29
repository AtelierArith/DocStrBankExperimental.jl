```julia
CVres(s::String) =
     CVres(s, nothing, nothing, nothing, nothing, nothing,
           nothing, nothing, nothing, nothing, nothing, nothing)
```

`.cvtype`フィールドのみを指定してCVres構造体のインスタンスを構築します。他のすべてのフィールドは`nothing`で埋められます。これは、手動でcrvalオブジェクトを構築するのに便利です。
