```
aws_profile_collection_release(collection)
```

Decrements a profile collection's ref count. When the ref count drops to zero, the collection will be destroyed. Returns NULL.

### Prototype

```c
struct aws_profile_collection *aws_profile_collection_release(struct aws_profile_collection *collection);
```
