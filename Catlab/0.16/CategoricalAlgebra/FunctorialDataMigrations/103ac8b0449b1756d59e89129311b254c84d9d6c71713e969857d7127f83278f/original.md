The subobject classifier Ω in a presheaf topos is the presheaf that sends each  object A to the set of sieves on it (equivalently, the set of subobjects of the  representable presheaf for A). Counting subobjects gives us the *number* of A  parts; the hom data for f:A->B for subobject Aᵢ is determined via:

Aᵢ ↪ A  ↑    ↑ f*   PB⌝↪ B          (PB picks out a subobject of B, up to isomorphism.)

(where A and B are the representables for objects A and B and f* is the unique  map from B into the A which sends the point of B to f applied to the point of A)

Returns the classifier as well as a dictionary of subobjects corresponding to  the parts of the classifier.
