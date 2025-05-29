```
offload(fun1, mgr::LoopManager, range, args...)
offload(fun2, mgr::LoopManager, (irange, jrange), args...)
```

Given a function performing a loop / loop nest:

```
    function fun1(range, args...)
        # do some computation shared by all indices i
        for i irange
            # do some work at index i
        end
        return Nothing
    end

    function fun2((irange, jrange), args...)
        # do some computation shared by all indices i,j
        for j in jrange
            # do some computation shared by all indices i
            for i irange
                # do some work at index i
            end
        end
        return Nothing
    end
```

Executes the loop nest with the provided manager. Depending on the manager, `fun` may be called just once on the full range, several times on sub-ranges, or many times on 'ranges' consisting of a single index.

!!! warning
    Each call to fun() must be independent, and several calls may occur concurrently. The only guarantee is that the whole iteration space is covered without overlap.


!!! note
    `offload` *may* amortize the cost of a pre-computation whose results are reused across iterations, as in the above example. This depends on how `offload` is implemented by the manager.

