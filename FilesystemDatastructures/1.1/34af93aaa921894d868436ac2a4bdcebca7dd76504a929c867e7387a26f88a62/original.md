```
hit!(fc::FileCache, key)
```

Returns `true` if the key exists within the cache, `false` otherwise.  Increments access counters for the given key, recording last access time, number of times accessed, etc...
