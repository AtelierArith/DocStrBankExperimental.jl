Marked(x<:Signed)   ⇢ x<:MarkableSigned    && ismarked(x)    Marked(x<:Unsigned) ⇢ x<:MarkableUnsigned  && ismarked(x)

```julia
three = 3
3
marked_three = Marked(three)
3
ismarked(marked_three)
true
!isunmarked(marked_three)
true
```
