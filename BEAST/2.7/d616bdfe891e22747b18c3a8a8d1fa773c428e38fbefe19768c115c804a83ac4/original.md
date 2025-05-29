```
real_inverse_z_transform(k, rho, N, X)
```

Returns the k-th term of the inverse z-transform. It is assumed that X[n+1] = conj(X[N-n]) for each n in 1:(N-1) so that Nmax = N/2+1 or (N+1)/2 (resp. if N%2==0 or N%2==1) terms are used in X X is an array of the z-transform evaluated in the points z=rho*exp(2*im*pi*n/N) for n in 0:(Nmax-1).
