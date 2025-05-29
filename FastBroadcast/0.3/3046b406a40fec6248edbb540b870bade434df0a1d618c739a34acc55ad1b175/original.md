```
@.. [thread=false] [broadcast=false] expr
```

`@..` turns `expr` into a broadcast-like expression, similar to `@.`. It additionally provides two optional keyword arguments:

  * thread: Defaults to `false`. Use multithreading?
  * broadcast: Defaults to `false`. If `true`, it will broadcast axes with dynamic   runtime sizes of `1` to larger sizes, if `false` only sizes known to be `1`   at compile time will be supported, i.e. axes such that   `ArrayInterface.known_length(typeof(StaticArrayInterface.static_axes(x,i))) == 1` will   be broadcast. Note that this differs from base broadcasting, in that   base broadcasting only supports `broadcast=true`.
