```
struct HomSpace{S<:ElementarySpace, P1<:CompositeSpace{S}, P2<:CompositeSpace{S}}
    codomain::P1
    domain::P2
end
```

Represents the linear space of morphisms with codomain of type `P1` and domain of type `P2`. Note that HomSpace is not a subtype of VectorSpace, i.e. we restrict the latter to denote certain categories and their objects, and keep HomSpace distinct.
