```
register_informat(f)
```

関数 `f` を `filereader` で使用するためのインフォーマットとして登録します。

> `filereader` 関数は `f` の最新の定義を使用しますが、ユーザーはアロケーションを避けるために `f` を変更するたびに再登録する必要があります。


# 例

```jldoctest
julia> function new_infmt!(x)
            replace!(x, "Y"=>"1")
        end
new_infmt! (generic function with 1 method)

julia> register_informat(new_infmt!)
[ Info: Informat new_infmt! has been registered

```
