```
mutable struct ClientBootstrap
    ptr::Ptr{aws_client_bootstrap}
end
```

Handles creation and setup of client socket connections.

Note on advanced use: the internal constructor on this struct has been left at its default so that you can bring your own native data if you need to. However, you are then responsible for the memory management of that data.
