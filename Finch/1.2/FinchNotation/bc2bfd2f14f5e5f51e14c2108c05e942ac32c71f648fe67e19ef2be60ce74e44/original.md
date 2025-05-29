```
walk(i)
```

The walk protocol usually iterates over each pattern element of a tensor in order. Note that the walk protocol "imposes" the structure of its argument on the kernel, so that we specialize the kernel to the structure of the tensor.
