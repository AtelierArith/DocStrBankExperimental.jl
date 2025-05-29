Type used to represent a "branch" of a dynamic. The branch is represented by a map `f` with domain `X=(a,b)`. X[1] and X[2] are interval enclosures of a,b.

The map must be monotonic on [a,b]. Note that this is not the same thing as being monotonic on hull(X[1], X[2]):  for instance, take the map x → (x-√2)^2 on [√2, 1]: the left endpoint X[1] will be prevfloat(√2)..nextfloat(√2),  but then the map is not monotonic on the whole hull(X[1], X[2]) because it also contains points that lie left of √2. This is a tricky case that must be dealt with.

Enclosures `Y[1], Y[2]` for f(a), f(b) and `increasing` may be provided (for instance if we know that `Y=(0,1)`), otherwise they are computed automatically.
