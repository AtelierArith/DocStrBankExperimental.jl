```
EASI(; max_harmonic::Int = 10, dct_method::Bool = false)
```

  * `max_harmonic`: Maximum harmonic of the input frequency for which the output power spectrum is analyzed for. Defaults to 10.
  * `dct_method`: Use Discrete Cosine Transform method to compute the power spectrum. Defaults to false.

## Method Details

The EASI method is a Fourier-based technique for performing variance-based methods of global sensitivity analysis for the computation of first order effects (Sobol' indices), hence belonging into the same class of algorithms as FAST and RBD. It is a computationally cheap method for which existing data can be used. Unlike the FAST and RBD methods which use a specially generated sample set that contains suitable frequency data for the input factors, in EASI these frequencies are introduced by sorting and shuffling the available input samples.

## API

```
gsa(f, method::EASI, p_range; samples, batch = false)
gsa(X, Y, method::EASI)
```

### Example

```julia
using GlobalSensitivity, Test

function ishi_batch(X)
    A= 7
    B= 0.1
    @. sin(X[1,:]) + A*sin(X[2,:])^2+ B*X[3,:]^4 *sin(X[1,:])
end
function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

lb = -ones(4)*π
ub = ones(4)*π

res1 = gsa(ishi,EASI(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,EASI(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)

X = QuasiMonteCarlo.sample(15000, lb, ub, QuasiMonteCarlo.SobolSample())
Y = ishi.([X[:, i] for i in 1:15000])

res1 = gsa(X, Y, EASI())
res1 = gsa(X, Y, EASI(; dct_method = true))
```
