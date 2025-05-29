```
CallocAllocator()
```

Use [`Libc.calloc`](https://docs.julialang.org/en/v1/base/libc/#Base.Libc.calloc) to allocate an array. This is similar to `zeros`, except that the Libc implementation or the operating system may allocate and zero the memory in a lazy fashion.

See also https://en.cppreference.com/w/c/memory/calloc .
