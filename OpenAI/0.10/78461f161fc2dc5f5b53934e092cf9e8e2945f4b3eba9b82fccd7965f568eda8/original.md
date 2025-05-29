modify thread

```julia
# Create a thread
thread_id = create_thread(api_key, [
    Dict("role" => "user", "content" => "Hello, how are you?")
]).response.id

# Modify the thread
modify_thread(api_key, thread_id, metadata=Dict("key" => "value"))
```
