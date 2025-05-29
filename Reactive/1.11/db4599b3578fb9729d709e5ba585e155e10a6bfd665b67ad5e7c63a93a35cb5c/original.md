`push!(signal, value, onerror=Reactive.print_error)`

Queue an update to a signal. The update will be propagated when all currently queued updates are done processing.

The third (optional) argument, `onerror`, is a callback triggered when the update ends in an error. The callback receives 4 arguments, `onerror(sig, val, node, capex)`, where `sig` and `val` are the Signal and value that `push!` was called with, respectively, `node` is the Signal whose action triggered the error, and `capex` is a `CapturedException` with the fields `ex` which is the original exception object, and `processed_bt` which is the backtrace of the exception.

The default error callback will print the error and backtrace to stderr.
