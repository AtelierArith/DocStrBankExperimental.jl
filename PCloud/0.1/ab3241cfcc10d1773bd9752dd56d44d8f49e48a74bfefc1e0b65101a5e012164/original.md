```
file_lock(client::PCloudClient; kwargs...)
```

Locks or unlocks a file descriptor `fd`.

This method works, depending on the `type` paramater:

  * `0`: release a lock
  * `1`: get a shared lock
  * `2`: get an exclusive lock

If the `offset` parameter is provided, only bytes starting from this offset are locked.

If the `length` parameter is provided, only `length` bytes starting from `offset` are locked. Length of 0 means lock until the end of file (no matter how big it grows).

The offset of this method could be interpreted depending on `whence` parameter:- `0`: offset is from the start of the file

  * `1`: offset is from current offset
  * `2`: offset is from the end of the file

If the parameter `get` is set, then instead of acquiring the lock only a test is performed if the file region can be locked.

By default locks are blocking, that is the call will block until the lock is granted (except when `get` is set or request is for unlocking). If you do not wish the lock to block, set the `noblock` parameter.

Locks are advisory locks, that is, they are not enforced on readers/writers that are not trying to take a lock.

You may hold just one lock on a file region. If shared lock is to be converted to an exclusive lock, the conversion is not atomic - the shared lock MIGHT be released first, before acquiring the exclusive lock. That happens only if the request for the exclusive lock can not be satisfied at the moment. This is done to prevent two processes from deadlocking by first holding a shared lock on a file and later trying to convert it to an exclusive lock. Processes still can deadlock by acquiring TWO locks simultaneously (each) on different files/regions in different order.

The API servers do not perform any kind of deadlock detection.

Source: https://docs.pcloud.com/methods/fileops/file_lock.html

# Arguments

  * `fd::Int`: the file descriptor, which is locked or unlocked
  * `type::Int`: what operation is performed to the file lock

# Optional Arguments

  * `offset::Int`: lock only bytes, starting from this position (default for offset is 0)
  * `length::Int`: lock length bytes only, starting from offset (default for length is 0)
  * `whence::Int`: how to interpred the offset (default for whence is 0)
  * `get::Int`: if set, then only test is performed if the file region can be locked
  * `noblock::Int`: set, if you do not wish the lock to block

# Output

The call is always successful unless read/write error is encountered. Result will be 0 regardless if lock was granted or not.

One should check the return field `locked` to see if lock was granted. Unlocking always sets `locked` to true, the same goes for blocking requests, as they are always successful (sooner or later).

So with `result` of `0` checking the value of `locked` makes sense only for non-blocking locks and for `get` checks.

# Output Example

```
{
    result: 0,
    locked: true
}
```
