```
typediter(::Type{ET},iter::IT)
TypedIterator{IT,ET}
```

イテレータ `IT` の周りに薄いラッパーを構築し、eltype `ET` を返します。

# 例

```jldoctest; output=false
using SimpleTraits
x = [1,2,missing]
@traitfn fm(x::::IsEltypeSuperOfMissing)  = count(ismissing.(x))

gen = (2*xi for xi in x)  
eltype(gen) == Any
#fm(gen)  # MethodError

gent = typediter(eltype(x), 2*xi for xi in x)
eltype(gent) == eltype(x)
fm(gent) == 1
# output
true
```
