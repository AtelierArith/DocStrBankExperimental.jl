```
mul_red!(z::AbsSimpleNumFieldElem, x::AbsSimpleNumFieldElem, y::AbsSimpleNumFieldElem, red::Bool)
```

Multiply $x$ by $y$ and set the existing number field element $z$ to the result. Reduction modulo the defining polynomial is only performed if `red` is set to `true`. Note that $x$ and $y$ must be reduced. This function is provided for performance reasons as it saves allocating a new object for the result and eliminates associated garbage collection.
