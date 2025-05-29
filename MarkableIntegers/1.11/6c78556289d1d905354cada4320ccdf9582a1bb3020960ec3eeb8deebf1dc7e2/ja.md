Unmarked(x<:Signed)   ⇢ x<:MarkableSigned    && isunmarked(x)    Unmarked(x<:Unsigned) ⇢ x<:MarkableUnsigned  && isunmarked(x)

```julia
three = 3
3
unmarked_three = Unmarked(three)
3
isunmarked(unmarked_three)
true
!ismarked(unmarked_three)
true
```
