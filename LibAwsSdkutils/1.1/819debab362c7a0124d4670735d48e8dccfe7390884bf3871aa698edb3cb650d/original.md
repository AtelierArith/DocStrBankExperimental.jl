```
aws_profile_collection_acquire(collection)
```

Increments the reference count on the profile collection, allowing the caller to take a reference to it.

Returns the same profile collection passed in.

### Prototype

```c
struct aws_profile_collection *aws_profile_collection_acquire(struct aws_profile_collection *collection);
```
