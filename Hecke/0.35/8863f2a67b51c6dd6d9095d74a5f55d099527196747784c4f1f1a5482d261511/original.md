```
evaluate(x::FacElem{QQFieldElem}) -> QQFieldElem
evaluate(x::FacElem{ZZRingElem}) -> ZZRingElem
```

Expands or evaluates the factored element, i.e. actually computes the the element. Works by first obtaining a simplified version of the power product into coprime base elements.
