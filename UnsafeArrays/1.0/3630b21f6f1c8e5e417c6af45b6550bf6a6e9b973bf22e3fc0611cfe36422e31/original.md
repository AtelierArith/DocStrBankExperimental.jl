```
@uviews A B ... expr
```

Replace arrays `A`, `B`, ... by uview(`A`), uview(`B`), ... during execution of `expr`, while protecting the original arrays from garbage collection.

Equivalent to

```
GC.@preserve A B ... begin
    let A = uview(A), B = uview(B), ...
        expr
    end
end
```

The unsafe views must not be allowed to escape the scope of `expr`. The original arrays must not be resized/appended/etc. during the execution of `expr`.
