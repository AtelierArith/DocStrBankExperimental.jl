```
XPRSgetmessagestatus(prob, msgcode)::status
```

Retrieves the current suppression status of a message.

# Arguments

  * `prob::XPRSprob`: The problem to check for the suppression status of the message error code.
  * `msgcode::Integer`: The id number of the message.

# Return value

  * `status::Int32`: Non-zero if the message is not suppressed; `0` otherwise.

See also the documentation of the correponding function [XPRSgetmessagestatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmessagestatus.html) in the C API.
