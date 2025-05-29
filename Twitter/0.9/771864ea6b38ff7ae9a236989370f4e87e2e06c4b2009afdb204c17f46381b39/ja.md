get*user*timeline(; kwargs...) 特定のTwitterユーザーからのタイムラインツイートの配列オブジェクトを取得します。この関数は、希望する `count` に達するまで、またはAPIが尽きるまで、どちらか早い方までAPIを呼び出します。

# 例

```julia-repl
julia> get_user_timeline(screen_name = "twitter", count = 1000)
```
