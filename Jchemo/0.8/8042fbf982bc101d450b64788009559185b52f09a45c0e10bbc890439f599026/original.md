```
svmr(; kwargs...)
svmr(X, y; kwargs...)
```

Support vector machine for regression (Epsilon-SVR).

  * `X` : X-data (n, p).
  * `y` : Univariate y-data (n).

Keyword arguments:

  * `kern` : Type of kernel used to compute the Gram matrices.   Possible values are: `:krbf`, `:kpol`, `:klin`,    `:ktanh`. See below.
  * `gamma` : `kern` parameter, see below.
  * `coef0` : `kern` parameter, see below.
  * `degree` : `kern` parameter, see below.
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
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)
p = nco(X)

kern = :krbf ; gamma = .1
cost = 1000 ; epsilon = 1
model = svmr(; kern, gamma, cost, epsilon) 
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

####### Example of fitting the function sinc(x)
####### described in Rosipal & Trejo 2001 p. 105-106 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
kern = :krbf ; gamma = .1
model = svmr(; kern, gamma) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "True model")
lines!(ax, x, vec(pred), label = "Fitted model")
axislegend("Method")
f
```
