```
shmctl(id, cmd, buf)
```

performs the control operation specified by `cmd` on the System V shared memory segment whose identifier is given in `id`. The `buf` argument is a byte array large enough to store a `shmid_ds` C structure.

See also [`shminfo`](@ref), [`shmcfg`](@ref) and [`shmrm`](@ref).
