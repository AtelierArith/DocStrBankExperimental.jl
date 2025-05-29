```
MultiSelectMenu
```

A menu that allows a user to select a multiple options from a list.

# Sample Output

```julia
julia> request(MultiSelectMenu(options))
Select the fruits you like:
[press: d=done, a=all, n=none, <enter>=select]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```
