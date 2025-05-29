```
prune_catchments(catchments, minsize; val=0)
```

minsizeより小さいすべての集水域を`val`（=0）に設定します。数が<1の集水域は無視されます。

集水域が再番号付けされるため、番号はもはや沈殿物や落とし穴に対応しないことに注意してください。
