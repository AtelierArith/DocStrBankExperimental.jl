`GarsideMonoid{T}`  is the abstract  type of Garside  monoids, where `T` is the type of simples. Such a monoid `M` should implement the same methods as `LocallyGarsideMonoid`  except  that  `isrightascent(M,a)` is automatically defined as `isleftdescent(M,\(M,a,M.δ),i)`.

An implementation should have fields `M.δ`, `M.stringδ`

An interval monoid should have a field `M.orderδ`.
