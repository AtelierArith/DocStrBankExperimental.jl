```
mutable struct EventLoopGroup
    ptr::Ptr{aws_event_loop_group}
end
```

A collection of event-loops. An event-loop is a thread for doing async work, such as I/O.

Note on advanced use: the internal constructor on this struct has been left at its default so that you can bring your own native data if you need to. However, you are then responsible for the memory management of that data.
