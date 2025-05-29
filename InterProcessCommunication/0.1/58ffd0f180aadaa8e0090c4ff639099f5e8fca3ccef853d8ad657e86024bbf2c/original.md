```
id = shmget(key, siz, flg)
```

yields the identifier of the System V shared memory segment associated with the System V IPC key `key`. A new shared memory segment with size `siz` (in bytes, possibly rounded up to a multiple of the memory page size `IPC.PAGE_SIZE`) is created if `key` has the value `IPC.PRIVATE` or if bit `IPC_CREAT` is set in `flg` and no shared memory segment corresponding to `key` exists.

Argument `flg` is a bitwise combination of flags. The least significant 9 bits specify the permissions granted to the owner, group, and others. These bits have the same format, and the same meaning, as the mode argument of `chmod`. Bit `IPC_CREAT` can be set to create a new segment. If this flag is not used, then `shmget` will find the segment associated with `key` and check to see if the user has permission to access the segment. Bit `IPC_EXCL` can be set in addition to `IPC_CREAT` to ensure that this call creates the segment. If `IPC_EXCL` and `IPC_CREAT` are both set, the call will fail if the segment already exists.
