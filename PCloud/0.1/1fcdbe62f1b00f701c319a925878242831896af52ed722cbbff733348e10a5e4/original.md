```
collection_move(client::PCloudClient; kwargs...)
```

Changes the position of an item in a given colleciton, owned by the current user.

Source: https://docs.pcloud.com/methods/collection/collection_move.html

# Arguments

  * `collectionid::Int`: the id of the collection.
  * `item::Int`: the position of the item in the collection.
  * `fileid::Int`: the id of the file to be moved in the collection.
  * `position::Int`: the position to which the items to be placed.

# Output Example

```
{
    "result": 0
}
```
