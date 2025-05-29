```
simplify(K::AbsSimpleNumField; canonical::Bool = false) -> AbsSimpleNumField, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

Tries to find an isomorphic field $L$ given by a "simpler" defining polynomial. By default, "simple" is defined to be of smaller index, testing is done only using a LLL-basis of the maximal order.

If `canonical` is set to `true`, then a canonical defining polynomial is found, where canonical is using the definition of PARI's `polredabs`, which is described in http://beta.lmfdb.org/knowledge/show/nf.polredabs.

Both versions require a LLL reduced basis for the maximal order.
