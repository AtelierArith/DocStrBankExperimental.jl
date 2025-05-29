```
isfiniteorder(m::MonoidElement)
```

Return `true` if `m` is of finite order, possibly without computing it.

!!! note
    If finiteness of a group or monoid can be decided based on its type there is no need to extend `isfiniteorder` for its elements.

