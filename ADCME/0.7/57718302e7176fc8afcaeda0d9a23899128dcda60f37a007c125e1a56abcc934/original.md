```
gradient_checkpointing(type::String="speed")
```

Uses checkpointing scheme for gradients. 

  * 'speed':  checkpoint all outputs of convolutions and matmuls. these ops are usually the most expensive,   so checkpointing them maximizes the running speed   (this is a good option if nonlinearities, concats, batchnorms, etc are taking up a lot of memory)
  * 'memory': try to minimize the memory usage   (currently using a very simple strategy that identifies a number of bottleneck tensors in the graph to checkpoint)
  * 'collection': look for a tensorflow collection named 'checkpoints', which holds the tensors to checkpoint
