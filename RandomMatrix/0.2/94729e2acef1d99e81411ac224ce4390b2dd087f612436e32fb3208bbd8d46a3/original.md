```julia
# Example

# The resolvent of a random Hermitian matrix is approximately diagonal, 
# see Section 3 in https://arxiv.org/pdf/1903.10060.pdf
 normview(resolvent(randHermitian(1000,norm=true))(0.5+0.1im))
```
