```
umask(msk) -> old
```

sets the calling process's file mode creation mask (`umask`) to `msk & 0o0777` (i.e., only the file permission bits of mask are used), and returns the previous value of the mask.

See also [`IPC.maskmode`](@ref).
