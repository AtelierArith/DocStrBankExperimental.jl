```
imap(f, xs1, [xs2, ...])
```

Iterate over values of a function applied to successive values from one or more iterators. Like `Iterators.zip`, the iterator is done when any of the input iterators have been exhausted.

```jldoctest
julia> for i in imap(+, [1,2,3], [4,5,6])
            @show i
       end
i = 5
i = 7
i = 9
```
