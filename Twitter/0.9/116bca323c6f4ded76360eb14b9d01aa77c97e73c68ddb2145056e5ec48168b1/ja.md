get*followers*ids(; kwargs...) 特定のTwitterユーザーからフォロワーIDのDictオブジェクトを取得します。この関数は、許可されている回数だけAPIを呼び出すか、または希望する `max_records` に達するまで、どちらか早い方を実行します。

# 例

```julia-repl
julia> get_followers_ids(screen_name = "jack", count = 10_000)
Dict{String,Any} with 6 entries:
  "previous_cursor_str" => "0"
  ...
```
