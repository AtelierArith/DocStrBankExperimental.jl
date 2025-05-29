Compute the Yoneda embedding of a category C in the category of C-sets.

Because Catlab privileges copresheaves (C-sets) over presheaves, this is the *contravariant* Yoneda embedding, i.e., the embedding functor C^op → C-Set.

The first argument `cons` is a constructor for the ACSet, such as a struct acset type. If representables have already been computed (which can be expensive), they can be supplied via the `cache` keyword argument.

Returns a `FinDomFunctor` with domain `op(C)`.
