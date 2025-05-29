```
timeouts(handle::FT_HANDLE, timeout_rd, timeout_wr)
```

Set the timeouts of an open [`FT_HANDLE`](@ref) using [`FT_SetTimeouts`](@ref).

Behaviour is undefined for `timeout_rd` = 0 and `timeout_wr` = 0.  `timeout_rd` = 0 appears to cause [`read`](@ref) and [`readavailable`](@ref) to  block.

See also: [`isopen`](@ref), [`open`](@ref)
