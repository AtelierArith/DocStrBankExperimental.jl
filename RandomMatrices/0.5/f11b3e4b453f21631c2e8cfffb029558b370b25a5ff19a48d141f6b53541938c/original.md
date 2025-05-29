GaussianHermite{β} represents a Gaussian Hermite ensemble with parameter β.

Wigner{β} is a synonym.

Example of usage:

```
β = 2 #β = 1, 2, 4 generates real, complex and quaternionic matrices respectively.
d = Wigner{β} #same as GaussianHermite{β}

n = 20 #Generate square matrices of this size

S = rand(d, n)       #Generate a 20x20 symmetric Wigner matrix
T = tridrand(d, n)   #Generate the symmetric tridiagonal form
v = eigvalrand(d, n) #Generate a sample of eigenvalues
```
