```
RadioMenu
```

A menu that allows a user to select a single option from a list.

# Sample Output

```julia
julia> request(RadioMenu(options, pagesize=4))
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```
