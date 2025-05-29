```
collection_delete(client::PCloudClient; kwargs...)
```

Delete a given collection owned by the current user.

System collections could not be deleted. In this case error `2065` (Collection not found.) will be raised.

Source: https://docs.pcloud.com/methods/collection/collection_delete.html

# Arguments

  * `collectionid::Int`: the id of the collection.

# Output Example

```
{
    "result": 0
}
```
