```
macro objectnames(category, names)
```

Defines a category name and its objects, along with pretty printing functionality.

# Examples

```julia @objectnames PMFC{2,1,0,1,0,0} 0 1 # without category name @objectnames Fib = UFC{2,1,0,2,0} I τ # with category name
