```
KRInfo
```

Kronecker-structure object definition. 

If `info::KRInfo` is the Kronecker-structure object, then:

`info.rki` is a vector whose components contains the right Kronecker indices;

`info.lki` is a vector whose components contains the left Kronecker indices;

`info.id` is a vector whose components contains the orders of the infinite elementary divisors (i.e., the multiplicities of infinite eigenvalues). 

`info.nf` is the number of finite eigenvalues.

`info.nrank` is the normal rank.

Destructuring via iteration produces the components `info.rki`, `info.lki`, `info.id`, `info.nf` and `info.nrank`.
