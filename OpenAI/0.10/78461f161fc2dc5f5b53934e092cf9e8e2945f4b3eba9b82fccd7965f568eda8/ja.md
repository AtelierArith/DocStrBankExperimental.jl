```julia
# スレッドを作成する
thread_id = create_thread(api_key, [
    Dict("role" => "user", "content" => "こんにちは、元気ですか？")
]).response.id

# スレッドを修正する
modify_thread(api_key, thread_id, metadata=Dict("key" => "value"))
```
