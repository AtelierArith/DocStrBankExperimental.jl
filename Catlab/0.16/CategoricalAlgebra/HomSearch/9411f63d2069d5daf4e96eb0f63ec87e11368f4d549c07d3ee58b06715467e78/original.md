Find all homomorphisms between two attributed $C$-sets via BackTracking Search.

take = number of homomorphisms requested (stop the search process early if this         number is reached) max = throw an error if we take more than this many morphisms (e.g. set max=1 if        one expects 0 or 1 morphism) filter = only consider morphisms which meet some criteria, expressed as a Julia           function of type ACSetTransformation -> Bool

It does not make sense to specify both `take` and `max`.
