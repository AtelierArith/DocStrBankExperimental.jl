PBPO matches consist of *two* morphisms. First, a match m: L → G, and secondly  a typing G → L′. With attributes, it is not so simple because G has concrete  values for attributes and L′ may have variables. Therefore, we actually change the  typing to map out of A, an abstracted version of G (with its attributes replaced  by variables). So we lift matches L->G to matches L->A, then search α∈Hom(A,L′).

In general, we want α to be uniquely determined by m, so by default `α_unique`   is set to true.

```
 m
```

L⌟ ⟶ G   ||     ↓ α   L  ⟶ L′      tl

```
 m
```

L ⟶ G  tl ↓ ↘a ↑ (abs = partial abstraction. Note `a` is `Labs` in the code.)    L′⟵ A        α

The "strong match" condition we enforce is that: tl⁻¹(α(A)) = a⁻¹(A). This means  we can deduce precisely what m is by looking at α.
