x = ssorPrecTrans!(A::SparseMatrixCSC,X::Array,B::Array,OmInvD::Vector=1 ./diag(A))

Applies SSOR steps to the linear systems A*X = B, for symmetric A. For efficiency, it works on the transpose of the matrix A.       

Input:

A       - sparse matrix CSC, assumed to be symmetric here   X       - current iterates   R       - residuals    OmInvD  - weighted diagional, that is, omega./diag(A)

Output: This method changes X and on the fly. The Array B is unchanged.

This version is well-suited as a preconditioner, for example, for CG.

Example for solving A*X=B, when A is Sparse Symmtric Positive definite:     omega = 1.2;     d = omega./diag(A);     x = zeros(length(d)) # pre allocation for the preconditioner result.     PC(r) = (x[:]=0.0; return ssorPrecTrans!(A,x,r,d));     y = KrylovMethods.cg(A,b,tol=1e-12,maxIter=200,M=PC,out=1)[1]
