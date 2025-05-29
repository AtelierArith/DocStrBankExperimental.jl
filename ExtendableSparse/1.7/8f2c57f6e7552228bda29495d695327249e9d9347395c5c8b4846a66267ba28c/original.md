```
allow_views(::preconditioner_type)
```

Factorizations on matrix partitions within a block preconditioner may or may not work with array views. E.g. the umfpack factorization cannot work with views, while ILUZeroPreconditioner can.  Implementing a method for `allow_views` returning `false` resp. `true` allows to dispatch to the proper case.
