Once the channel shuts down, this function will be invoked within the thread of the event-loop that the channel is assigned to.

Note: this function is only invoked if the channel was successfully setup, e.g. [`aws_server_bootstrap_on_accept_channel_setup_fn`](@ref)() was invoked without an error code.
