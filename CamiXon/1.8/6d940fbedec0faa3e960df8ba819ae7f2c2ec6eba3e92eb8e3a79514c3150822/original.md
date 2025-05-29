```
Def(T, atom, spinorbit, pot, scr, o1, o2, o3, pos, epn, k, am, matLD)
```

Type with fields:

  * `.atom::Atom`             : atom object
  * `.spinorbit::Spinorbit`    : spinorbit object
  * `.codata::Codata`           : codata object
  * `.pot::Vector{T}`        : tabulated potential function
  * `.scr::Vector{T}`        : tabulated screening function
  * `.potscr::Vector{T}`        : tabulated screened potential function
  * `.G::Vector{Matrix{T}}`: vector of zero-filled matrices
  * `.σ::Vector{Matrix{T}}`: vector of zero-filled matrices
  * `.Minv::Vector{Matrix{T}}`: vector of zero-filled matrices
  * `.pos::Pos`              : object with fields Na, Nlctp, Nmin, Nuctp, Nb, N and nodes
  * `.epn::Int`              : number of endpoints trapezoidal correction - must be odd
  * `.k::Int`              : Adams-Moulton order
  * `.am::Vector{T}`        : Adams-Moulton weight coefficients
  * `.matLD::Matrix{T}`        : Lagrangian differentiation matrix

The object `Def` is best created with the function [`castDef`](@ref).
