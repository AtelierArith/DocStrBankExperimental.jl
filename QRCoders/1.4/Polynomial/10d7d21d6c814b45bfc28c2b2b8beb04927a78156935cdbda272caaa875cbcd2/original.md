```
generator_matrix(msglen::Int, necwords::Int)
```

Create the generator matrix of size `(msglen + necwords, msglen)`.

The generator matrix G is of the form

```
[ * ]
[ I ]
```

where `I` is the identity matrix of size `msglen` and `*` is computed by the remainder polynomials.

Note that we use a reversed version of generator matrices, i.e. the coefficients is stored in the reverse order,  e.g. a*0, ..., a*n.

In this sense, we still have G⋅x = c, where x is the message polynomial  and c is the received polynomial.

To get an ordinary generator matrix, just rotate it by 180 degrees, i.e. @view(G[end:-1:1, end:-1:1])
