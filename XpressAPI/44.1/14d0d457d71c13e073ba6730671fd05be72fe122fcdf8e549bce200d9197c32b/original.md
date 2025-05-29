```
XPRS_ge_getlasterror(maxbytes)::msgcode, msg, nbytes
```

Returns the last error encountered during a call to the Xpress global environment.

# Arguments

  * `maxbytes::Integer`: The size of the character buffer `msg`.

# Return values

  * `msgcode::Int32`: Memory location in which the error code will be returned.
  * `msg::AbstractString`: A character buffer of size `maxbytes` in which the last error message relating to the global environment will be returned.
  * `nbytes::Int32`: Memory location in which the minimum required size of the buffer to hold the full error string will be returned.

See also the documentation of the correponding function [XPRS*ge*getlasterror](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_ge_getlasterror.html) in the C API.
