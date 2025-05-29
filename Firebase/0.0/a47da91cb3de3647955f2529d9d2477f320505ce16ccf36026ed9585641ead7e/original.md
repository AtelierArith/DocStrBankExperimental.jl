realdb*post(url, body = "{"name": "real*db_test"}"; query = Dict())

POST request to an endpoint.

# Example

```julia
realdb_init("https://[PROJECT_ID].asia-southeast1.firebasedatabase.app")
# realdb_post("/message_list")
body =Dict("user_id" => "jack", "text" => "Ahoy!")
realdb_post("/message_list",body)
```

## Notes:

According to the REST API documentation for Realtime Database,  a POST is the equivalent of a "push" operation when using the client SDKs. This push operation always involves adding data under a random ID.  There is no avoiding that for a push.

If you know the name of the node where you want to add data, you should use a PUT instead. This is the equivalent of using "set" operation with the client SDKs.
