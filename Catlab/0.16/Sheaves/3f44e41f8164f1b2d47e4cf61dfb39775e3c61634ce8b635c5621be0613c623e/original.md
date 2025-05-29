```
restrict(X::AbstractSheaf, s::Data, f::Hom) where {Data, Hom}
```

Restrict a section along a morphism in the sheaf. This is to apply the sheaf's functor to the morphism f and then apply that function to the data supplied.  We can assume that you can directly call that applied functor on data, because sheaves take C to **Set**.
