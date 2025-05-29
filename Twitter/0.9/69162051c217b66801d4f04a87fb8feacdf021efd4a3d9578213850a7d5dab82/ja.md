get*friends*ids(; kwargs...) 特定のTwitterユーザーからフォロワーIDのDictオブジェクトを取得します。この関数は、希望する`count`に達するまで、またはAPIが尽きるまで、どちらか早い方でAPIを呼び出します。

# 例

```julia-repl
julia> get_friends_ids(screen_name = "barackobama", count = 1000)
```
