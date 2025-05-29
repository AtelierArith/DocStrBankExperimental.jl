```
guess(R::QQBarField, x::AcbFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::ArbFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::ComplexFieldElem, maxdeg::Int, maxbits::Int=0)
guess(R::QQBarField, x::RealFieldElem, maxdeg::Int, maxbits::Int=0)
```

Try to reconstruct an algebraic number from a given numerical enclosure `x`. The algorithm looks for candidates up to degree `maxdeg` and with coefficients up to size `maxbits` (which defaults to the precision of `x` if not given). Throws if no suitable algebraic number can be found.

Guessing typically requires high precision to succeed, and it does not make much sense to call this function with input precision smaller than $O(maxdeg \cdot maxbits)$. If this function succeeds, then the output is guaranteed to be contained in the enclosure `x`, but failure does not prove that such an algebraic number with the specified parameters does not exist.

This function does a single iteration with the target parameters. For best performance, one should invoke this function repeatedly with successively larger parameters when the size of the intended solution is unknown or may be much smaller than a worst-case bound.
