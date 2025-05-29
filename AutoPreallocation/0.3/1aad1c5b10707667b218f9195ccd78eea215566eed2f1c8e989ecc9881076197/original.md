```
preallocate(f, xs...)
```

Return the first run result and a preallocated version of the corresponding method of callable object `f` given its argument. Note the behaviour of both the method generated record and the method will be freezed, you shouldn't feed this function with a dynamic allocation method.
