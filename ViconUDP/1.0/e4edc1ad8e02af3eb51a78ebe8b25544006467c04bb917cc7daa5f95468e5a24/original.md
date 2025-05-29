```
start_async_read(vicon::ViconSystem, ItemName::String, buffer_size = 10)
```

Starts a asyncron read from Vicon System. Returns a function that returns the latest item. buffer_size is the size of the Channel sending data from the async task.
