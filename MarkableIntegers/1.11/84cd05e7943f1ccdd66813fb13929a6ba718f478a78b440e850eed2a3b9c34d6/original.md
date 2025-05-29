```julia
three = 3
3
markable_three = Unmarked(three)
3
isunmarked(markable_three)
true
@mark!(markable_three)
3
ismarked(markable_three)
true
```
