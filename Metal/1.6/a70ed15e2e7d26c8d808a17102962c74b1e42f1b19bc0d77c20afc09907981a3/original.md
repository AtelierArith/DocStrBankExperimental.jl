```
synchronize(queue)
```

Wait for currently committed GPU work on this queue to finish.

Create a new MTLCommandBuffer from the global command queue, commit it to the queue, and simply wait for it to be completed. Since command buffers *should* execute in a First-In-First-Out manner, this synchronizes the GPU.
