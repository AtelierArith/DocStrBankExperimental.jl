```
CatNumDiscriminator(
   Dict(
      :name => "catnumdisc",
      :maxcategories => 24
   )
)
```

Transform numeric columns to string (as categories)  if the count of their unique elements <= maxcategories.

Implements `fit!` and `transform!`.
