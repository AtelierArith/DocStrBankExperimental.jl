Subroutine dtrpcg

Given a sparse symmetric matrix A in compressed column storage, this subroutine uses a preconditioned conjugate gradient method to find an approximate minimizer of the trust region subproblem

min { q(s) : || L'*s || <= delta }.

where q is the quadratic

q(s) = 0.5*s'*A*s + g'*s,

A is a symmetric matrix in compressed column storage, L is a lower triangular matrix in compressed column storage, and g is a vector.

This subroutine generates the conjugate gradient iterates for the equivalent problem

min { Q(w) : || w || <= delta },

where Q is the quadratic defined by

Q(w) = q(s),        w = L'*s.

Termination occurs if the conjugate gradient iterates leave the trust regoin, a negative curvature direction is generated, or one of the following two convergence tests is satisfied.

Convergence in the original variables:

|| grad q(s) || <= tol

Convergence in the scaled variables:

|| grad Q(w) || <= stol

Note that if w = L'*s, then L*grad Q(w) = grad q(s).

MINPACK-2 Project. March 1999. Argonne National Laboratory. Chih-Jen Lin and Jorge J. More'.

August 1999

Corrected documentation for l, ldiag, lcol*ptr, and lrow*ind.

February 2001

We now set iters = 0 in the special case g = 0.
