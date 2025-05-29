`@curry exprs...`

最後の引数のすべての第一レベルメソッド呼び出しに`exprs`を最初の引数として注入します。[`curry`](@ref)のようですが、他のメソッドに渡すことができる匿名メソッドインスタンスは生成しません。

# 例

```julia
logid = 42
@curry "Log " logid ": " begin
   println(420)
   println(69)
end
# "Log 42: 420"と表示されます
# "Log 42: 69"と表示されます
```
