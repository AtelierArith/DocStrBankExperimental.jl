```
alloc(device, bytesize, [ptr=nothing];
      storage=Default, hazard_tracking=Default, cache_mode=Default)
```

Allocates a Metal buffer on `device` of`bytesize` bytes. If a CPU-pointer is passed as last argument, then the buffer is initialized with the content of the memory starting at `ptr`, otherwise it's zero-initialized.

! Note: You are responsible for freeing the returned buffer

The storage kwarg controls where the buffer is stored. Possible values are:

  * PrivateStorage : Residing on the device
  * SharedStorage  : Residing on the host
  * ManagedStorage : Keeps two copies of the buffer, on device and on host. Explicit calls must be given to syncronize the two
  * Memoryless : an iOS specific thing that won't work on Mac.

Note that `PrivateStorage` buffers can't be directly accessed from the CPU, therefore you cannot use this option if you pass a ptr to initialize the memory.
