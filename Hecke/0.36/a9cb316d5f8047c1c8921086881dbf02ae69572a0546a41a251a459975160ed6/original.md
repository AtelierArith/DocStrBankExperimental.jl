```
push_through_isogeny(f::Isogeny, v::RingElem) -> RingElem
```

Let $f:E \to E'$ be an isogeny and let S be the set of points on E whose x-coordinate is a root of v. Assume that the kernel polynomial of f divides v. Return the polynomial psi whose roots are exactly the x-coordinates of the points $Q$ in $f(S)$.
