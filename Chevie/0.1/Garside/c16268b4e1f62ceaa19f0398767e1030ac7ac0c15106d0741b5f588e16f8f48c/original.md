`LocallyGarsideMonoid{T}`  is the abstract type of locally Garside monoids, where  `T`  is  the  type  of  simples.  Such a monoid `M` needs, for `a,b` simples, to implement the functions

  * `one(M)`
  * `isleftdescent(M,a,i::Int)`  whether `M.atoms[i]≼ a`
  * `isrightdescent(M,a,i::Int)` whether `a≽ M.atoms[i]`
  * `isrightascent(M,a,i::Int)`  whether `a*M.atoms[i]` is simple
  * `*(M,a,b)`  when `a*b` is simple returns the simple `a*b`
  * `\(M,a,b)` when `a≼ b` returns the simple `a`
  * `/(M,a,b)`  when `a≽ b` returns the simple `a/b`
