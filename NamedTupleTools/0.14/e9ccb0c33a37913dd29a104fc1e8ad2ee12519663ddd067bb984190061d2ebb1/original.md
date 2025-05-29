```
merge_recursive(nt1, nt2)
merge_recursive(nt1, nt2, nt3, ..)
```

Recursively merge namedtuples. Where more than one of the namedtuple args share the same fieldname (same key),     the rightmost argument's key's value will be propogated. Where each namedtuple has distinct fieldnames (keys),     all of named fields will be gathered with their respective values. The named fields will appear in the same     order they are encountered (rightmost arg, second rightmost arg, .., second leftmost arg, leftmost arg).

If there are no nested namedtuples, `merge(nt1, nts..., recursive=true)` is the same as `merge(nt1, nts...)`.

```
a = (food = (fruits = (orange = "mango", white = "pear"),
             liquids = (water = "still", wine = "burgandy")))

b = (food = (fruits = (yellow = "banana", orange = "papaya"),
             liquids = (water = "sparkling", wine = "champagne"),
             bread = "multigrain"))

merge(b,a)  == (fruits  = (orange = "mango", white = "pear"),
                liquids = (water = "still", wine = "burgandy"),
                bread   = "multigrain")

merge_recursive(b,a) ==
               (fruits  = (yellow = "banana", orange = "mango", white = "pear"),
                liquids = (water = "still", wine = "burgandy"),
                bread   = "multigrain")

merge(a,b)  == (fruits  = (yellow = "banana", orange = "papaya"),
                liquids = (water = "sparkling", wine = "champagne"),
                bread   = "multigrain")

merge_recursive(a,b) ==
               (fruits  = (orange = "papaya", white = "pear", yellow = "banana"),
                liquids = (water = "sparkling", wine = "champagne"),
                bread   = "multigrain")
```

see: [`merge`](@ref)
