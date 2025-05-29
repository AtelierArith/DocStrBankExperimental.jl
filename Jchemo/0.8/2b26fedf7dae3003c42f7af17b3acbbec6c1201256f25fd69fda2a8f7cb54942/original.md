```
svmda(; kwargs...)
svmda(X, y; kwargs...)
```

Support vector machine for discrimination "C-SVC" (SVM-DA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).

Keyword arguments:

  * `kern` : Type of kernel used to compute the Gram matrices.   Possible values are: `:krbf`, `:kpol`, `:klin`,    `:ktanh`. See below.
  * `gamma` : `kern` parameter, see below.
  * `degree` : `kern` parameter, see below.
  * `coef0` : `kern` parameter, see below.
  * `cost` : Cost of constraints violation C parameter.
  * `epsilon` : Epsilon parameter in the loss function.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

Kernel types: 

  * :krbf – radial basis function: exp(-gamma * ||x - y||^2)
  * :kpol – polynomial: (gamma * x' * y + coef0)^degree
  * "klin – linear: x' * y
  * :ktan – sigmoid: tanh(gamma * x' * y + coef0)

The function uses LIBSVM.jl (https://github.com/JuliaML/LIBSVM.jl)  that is an interface to library LIBSVM (Chang & Li 2001).

## References

Julia package LIBSVM.jl: https://github.com/JuliaML/LIBSVM.jl

Chang, C.-C. & Lin, C.-J. (2001). LIBSVM: a library for support  vector machines. Software available at  http://www.csie.ntu.edu.tw/~cjlin/libsvm. Detailed documentation  (algorithms, formulae, ...) can be found in http://www.csie.ntu.edu.tw/~cjlin/papers/libsvm.ps.gz

Chih-Chung Chang and Chih-Jen Lin, LIBSVM: a library for support  vector machines. ACM Transactions on Intelligent Systems and  Technology, 2:27:1–27:27, 2011. Software available at  http://www.csie.ntu.edu.tw/~cjlin/libsvm

Schölkopf, B., Smola, A.J., 2002. Learning with kernels:  support vector machines, regularization, optimization, and  beyond. Adaptive computation and machine learning. MIT Press,  Cambridge, Mass.

## Examples

```julia
using Jchemo, JchemoData, JLD2
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/forages2.jld2")
@load db dat
@names dat
X = dat.X
Y = dat.Y
n = nro(X) 
s = Bool.(Y.test)
Xtrain = rmrow(X, s)
ytrain = rmrow(Y.typ, s)
Xtest = X[s, :]
ytest = Y.typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

kern = :krbf ; gamma = 1e4
cost = 1000 ; epsilon = .5
model = svmda(; kern, gamma, cost, epsilon) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
fitm.lev
fitm.ni

res = predict(model, Xtest) ; 
@names res 
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
