```
XPRSaddcbmessage(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function.
  * `msg`: A null terminated character array (string) containing the message, which may simply be a new line. The total number of bytes (including `NUL` terminator) will not exceed `XPRS_MAXMESSAGELENGTH`. If a message needs to be truncated to meet this limit, the last four bytes in `msg` are set to "...0".
  * `msglen`: The length of the message string, excluding the null terminator.
  * `msgtype`: Indicates the type of output message: 1information messages; 2(not used); 3warning messages; 4error messages.A negative value indicates that the Optimizer is about to finish and the buffers should be flushed at this time if the output is being redirected to a file.

`cb` will be invoked with this signature:

```
cb(cbprob, msg, msglen, msgtype)::Nothing
```
