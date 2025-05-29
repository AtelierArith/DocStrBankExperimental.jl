```
sc_hash
```

The [`sc_hash`](@ref) implements a hash table. It uses an array which has linked lists as elements.

| Field      | Note                                |
|:---------- |:----------------------------------- |
| elem_count | total number of objects contained   |
| slots      | the slot count is slots->elem_count |
| user_data  | user data passed to hash function   |
| allocator  | must allocate [`sc_link_t`](@ref)   |
