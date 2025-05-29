```
XPRSsetmessagestatus(prob, msgcode, status)::prob
```

Manages suppression of messages.

# Arguments

  * `prob::XPRSprob`: The problem for which message `msgcode` is to have its suppression status changed; pass `nothing` if the message should have the status apply globally to all problems.
  * `msgcode::Integer`: The id number of the message.
  * `status::Integer`: Non-zero if the message is not suppressed; `0` otherwise. If a value for `status` is not supplied in the command-line call then the console Optimizer prints the value of the suppression status to screen i.e., non-zero if the message is not suppressed; `0` otherwise.

# Return value

  * `prob::XPRSprob`: The problem for which message `msgcode` is to have its suppression status changed; pass `nothing` if the message should have the status apply globally to all problems.

See also the documentation of the correponding function [XPRSsetmessagestatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetmessagestatus.html) in the C API.
