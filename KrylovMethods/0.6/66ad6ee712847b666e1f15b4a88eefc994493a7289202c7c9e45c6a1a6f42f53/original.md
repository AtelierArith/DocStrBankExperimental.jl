U, B, V =  lanczosBidiag(A,p::Vector,k::Int)

Lanczos bidiagonalization of matrix A.

Input:

A       - function computing A*x = A(x,'F') and A'*x = A(x,'T')   p       - starting vector   k       - dimension of subspace

Output:

U,B,V   - Lanczos vectors
