```
RSA(; n_dummy_parameters::Int = 10, acceptance_threshold::Union{Function, Real} = mean)
```

  * `n_dummy_parameters`: Number of dummy parameters to add to the model, used for sensitivity hypothesis testing and to check the amount of samples. Defaults to 10.
  * `acceptance_threshold`: Threshold or function to compute the threshold for defining the acceptance distribution of the sensitivity outputs. The function must be of signature f(Y)   and return a real number, where Y is the output of given sensitivity criterion. Defaults to the mean of the sensitivity values.

## Method Details

The RSA (Regional Sensitivity Analysis) method[^1] is a monte-carlo based technique for performing nonparametric global sensitivity analysis. The method is based on the Kolmogorov-Smirnov (KS) test, which is a nonparametric test of the equality of continuous,  one-dimensional probability distributions. Each result of a monte-carlo simulation is either classified as behavior ($B$) or non-behavior ($\bar{B}$). For each parameter $i$,  the cumulative distributions of the behavior and non-behavior outputs are determined as $F_{i}$ and $\bar{F}_{i}$, respectively. The sensitivity for each parameter $i$ is then given by:

$$
S_{i} = \sup_{j} |F_{i,j} - (1 - F_{i,j})|
$$

where $F_{i,j}$ is sample $j$ of the cumulative distribution of the sensitivity output for parameter $i$.

Dummy parameters are added to the model to check the amount of samples and to perform sensitivity hypothesis testing. Note that because of random sampling the results may vary between runs. 

## API

```
gsa(f, method::RSA, p_range; samples, batch = false)
```

Returns a `RSAResult` object containing the sensitivity indices for the parameters as `S`, and mean and standard deviation of the dummy parameters as a tuple `Sd = (<mean>, <std>)`.

### Example

```julia
using GlobalSensitivity

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

res1 = gsa(ishi,RSA(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,RSA(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)
```

### References

[^1]: Hornberger, G.M. & Spear, Robert. (1981). An Approach to the Preliminary Analysis of Environmental Systems. J. Environ. Manage.; (United States). 12:1.
