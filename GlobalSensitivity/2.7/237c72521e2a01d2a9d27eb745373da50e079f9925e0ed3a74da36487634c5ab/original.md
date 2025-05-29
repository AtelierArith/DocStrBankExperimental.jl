MutualInformation(; n*bootstraps = 1000, conf*level = 0.95)

  * `n_bootstraps`: Number of bootstraps to be used for estimation of null distribution. Default is `1000`.
  * `conf_level`: Confidence level for the minimum bound estimation. Default is `0.95`.

## Method Details

The sensitivity analysis based on mutual information is an alternative approach to sensitivity analysis based on information theoretic measures. In this method, the output uncertainty is quantified by the entropy of the output distribution, instead of taking a variance-based approach. The Shannon entropy of the output is  given by:

$$
H(Y) = -\sum_y p(y) \log p(y)
$$

Where $p(y)$ is the probability density function of the output $Y$. By fixing an input $X_i$, the conditional entropy of the output $Y$ is given by:

$$
H(Y|X_i) = -\sum_{x} p(x) H(Y|X_i = x)
$$

The mutual information between the input $X_i$ and the output $Y$ is then given by:

$$
I(X_i;Y) = H(Y) - H(Y|X_i) = H(X) + H(Y) - H(X,Y)
$$

Where $H(X,Y)$ is the joint entropy of the input and output. The mutual information can be used to calculate the sensitivity indices of the input parameters. 

### Sensitivity Indices

The sensitivity indices are calculated as the mutual information between the input $X_i$ and the output $Y$ where the $\alpha$ quantile of null distribution of the output is subtracted from the mutual information:

$$
S_{1,i} = I(X_i;Y) - Q(I(X_i; Y_\text{null}), \alpha)
$$

Using mutual information for sensitivity analysis is introduced in Lüdtke et al. (2007)[^1] and also present in Datseris & Parlitz (2022)[^2]. 

## API

```
gsa(f, method::MutualInformation, p_range; samples, batch = false)
```

Returns a `MutualInformationResult` object containing the resulting sensitivity indices for the parameters and the corresponding confidence intervals. The `MutualInformationResult` object contains the following fields:

  * `S`: Sensitivity indices.
  * `mutual_information`: Computed mutual information values
  * `bounds`: Computed upper bounds of the null distribution of mutual information.

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

res1 = gsa(ishi,MutualInformation(),[[lb[i],ub[i]] for i in 1:4],samples=15000)
res2 = gsa(ishi_batch,MutualInformation(),[[lb[i],ub[i]] for i in 1:4],samples=15000,batch=true)
```

### References

[^1]: Lüdtke, N., Panzeri, S., Brown, M., Broomhead, D. S., Knowles, J., Montemurro, M. A., & Kell, D. B. (2007). Information-theoretic sensitivity analysis: a general method for credit assignment in complex networks. Journal of The Royal Society Interface, 5(19), 223–235.

[^2]: Datseris, G., & Parlitz, U. (2022). Nonlinear Dynamics, Ch. 7, pg. 105-119.
