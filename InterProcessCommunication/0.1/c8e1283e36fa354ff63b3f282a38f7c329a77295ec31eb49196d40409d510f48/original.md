```
id = ShmId(id)
id = ShmId(shm)
id = ShmId(arr)
id = ShmId(key; readlony=false)
```

yield the the identifier of the existing System V shared memory segment associated with the value of the first argument: `id` is the identifier of the shared memory segment, `shm` is a System V shared memory object, `arr` is an array attached to a System V shared memory segment, and `key` is the key associated with the shared memory segment. In that latter case, keyword `readlony` can be set `true` to request read-only access; otherwise read-write access is requested.

See also: [`shmid`](@ref), [`shmget`](@ref).
