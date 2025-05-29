```
manage_shards(; sort_by=:name, rev=false)
```

Open a prompt allowing a user to selectively remove downloaded compiler shards. By default, the shards are sorted by name, alternatively you can sort them by file size on disk by specifying `sort_by=:size`. With `rev=true` you can reverse the sort order.
