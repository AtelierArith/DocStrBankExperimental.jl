```
mlmnet_perms(data::RawData, 
                  lambdas::AbstractArray{Float64,1}, alphas::AbstractArray{Float64,1};
                  method::String = "ista", isNaive::Bool=false, 
                  permFun::Function=shuffle_rows, 
                  addXIntercept::Bool=true, addZIntercept::Bool=true, 
                  toXReg::BitArray{1}=trues(data.p), 
                  toZReg::BitArray{1}=trues(data.q), 
                  toXInterceptReg::Bool=false, 
                  toZInterceptReg::Bool=false, 
                  toNormalize::Bool=true, isVerbose::Bool=true, 
                  stepsize::Float64=0.01, setStepsize=true, funArgs...)
```

Permutes response matrix Y in RawData object and then calls the mlmnet core  function. 

# Arguments

  * data = RawData object
  * lambdas = 1d array of floats consisting of the total penalties in descending  order. If they are not in descending order, they will be sorted.
  * alphas = 1d array of floats consisting of the penalty ratio that  determines the mix of penalties between L1 and L2

# Keyword arguments

  * methods = function name that applies the Elastic-net penalty estimate method; default is `ista`, and the other methods are `fista`, `fista_bt`, `admm` and `cd`
  * isNaive = boolean flag indicating whether to solve the Naive or non-Naive  Elastic-net problem
  * permFun = function used to permute `Y`. Defaults to `shuffle_rows`  (shuffles rows of `Y`).
  * addXIntercept = boolean flag indicating whether or not to include an `X`  intercept (row main effects). Defaults to `true`.
  * addZIntercept = boolean flag indicating whether or not to include a `Z`  intercept (column main effects). Defaults to `true`.
  * toXReg = 1d array of bit flags indicating whether or not to regularize each  of the `X` (row) effects. Defaults to 2d array of `true`s with length  equal to the number of `X` effects (equivalent to `data.p`).
  * toZReg = 1d array of bit flags indicating whether or not to regularize each  of the `Z` (column) effects. Defaults to 2d array of `true`s with length  equal to the number of `Z` effects (equivalent to `data.q`).
  * toXInterceptReg = boolean flag indicating whether or not to regularize the  `X` intercept Defaults to `false`.
  * toZInterceptReg = boolean flag indicating whether or not to regularize the  `Z` intercept. Defaults to `false`.
  * toNormalize = boolean flag indicating if the columns of `X` and `Z`  should be standardized (to mean 0, standard deviation 1). Defaults to `true`.
  * isVerbose = boolean flag indicating whether or not to print messages.   Defaults to `true`.
  * setStepsize = boolean flag indicating whether the fixed step size should be  calculated (for `ista!` and `fista!`). Defaults to `true`.
  * stepsize = float; step size for updates (irrelevant for coordinate  descent and when `setStepsize` is set to `true` for `ista!` and `fista!`).  Defaults to `0.01`.
  * funArgs = variable keyword arguments to be passed into `fun`

# Value

An MLMnet object

# Some notes

The default method for choosing the fixed step size for `fista!` or `ista!`  is to use the reciprocal of the product of the maximum eigenvalues of  `X*transpose(X)` and `Z*transpose(Z)`. This is computed when `fista!` or  `ista!` is passed into the `fun` argument and `setStepsize` is set to `true`.  If `setStepsize` is set to `false`, the value of the `stepsize` argument will  be used as the fixed step size. Note that obtaining the eigenvalues when `X`  and/or `Z` are very large may exceed computational limitations. 

Specifying a good starting step size (`stepsize`) and multiplying factor  (`gamma`) when `fista_bt!` is passed into the `fun` argument can be difficult.  Shrinking the step size too gradually can result in slow convergence. Doing so  too quickly can cause the criterion to diverge. We have found that setting  `stepsize` to 0.01 often works well in practice; choice of `gamma` appears to  be less consequential. 
