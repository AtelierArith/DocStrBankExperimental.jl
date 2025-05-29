```
follow(i)
```

The follow protocol ignores the structure of the tensor. By itself, the follow protocol iterates over each value of the tensor in order, looking it up with random access.  The follow protocol may specialize on e.g. the zero value of the tensor, but does not specialize on the structure of the tensor. This enables efficient random access and avoids large code sizes.
