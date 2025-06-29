```
krr(; kwargs...)
krr(X, Y; kwargs...)
krr(X, Y, weights::Weight; kwargs...)
krr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Kernel ridge regression (KRR) implemented by SVD factorization.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `lb` : Ridge regularization parameter "lambda".
  * `kern` : Type of kernel used to compute the Gram matrices.   Possible values are: `:krbf`, `:kpol`. See respective    functions `krbf` and `kpol` for their keyword arguments.
  * `scal` : Boolean. If `true`, each column of `X    is scaled by its uncorrected standard deviation.

KRR is also referred to as least squared SVM regression  (LS-SVMR). The method is close to the particular case of  SVM regression where there is no marge excluding the  observations (epsilon coefficient set to zero). The difference  is that a L2-norm optimization is done, instead of L1 in SVM.

## References

Bennett, K.V., Embrechts, M.J., 2003. An optimization  perspective on kernel partial least squares regression,  in: Advances in Learning Theory: Methods, Models and  Applications, NATO Science Series III: Computer & Systems  Sciences. IOS Press Amsterdam, pp. 227-250.

Cawley, G.C., Talbot, N.L.C., 2002. Reduced Rank Kernel  Ridge Regression. Neural Processing Letters 16, 293-302.  https://doi.org/10.1023/A:1021798002258

Krell, M.M., 2018. Generalizing, Decoding, and Optimizing  Support Vector Machine Classification. arXiv:1801.04929.

Saunders, C., Gammerman, A., Vovk, V., 1998. Ridge Regression  Learning Algorithm in Dual Variables, in: In Proceedings of the  15th International Conference on Machine Learning. Morgan  Kaufitmann, pp. 515-521.

Suykens, J.A.K., Lukas, L., Vandewalle, J., 2000. Sparse  approximation using least squares support vector machines. 2000 IEEE  International Symposium on Circuits and Systems. Emerging Technologies  for the 21st Century. Proceedings (IEEE Cat No.00CH36353). https://doi.org/10.1109/ISCAS.2000.856439

Welling, M., n.d. Kernel ridge regression. Department of  Computer Science, University of Toronto, Toronto, Canada.  https://www.ics.uci.edu/~welling/classnotes/papers_class/Kernel-Ridge.pdf

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

lb = 1e-3
kern = :krbf ; gamma = 1e-1
model = krr(; lb, kern, gamma) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

coef(model)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
   ylabel = "Observed").f    

coef(model; lb = 1e-1)
res = predict(model, Xtest; lb = [.1 ; .01])
@head res.pred[1]
@head res.pred[2]

lb = 1e-3
kern = :kpol ; degree = 1
model = krr(; lb, kern, degree) 
fit!(model, Xtrain, ytrain)
res = predict(model, Xtest)
rmsep(res.pred, ytest)

####### Example of fitting the function sinc(x)
####### described in Rosipal & Trejo 2001 p. 105-106 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
lb = 1e-1
kern = :krbf ; gamma = 1 / 3
model = krr(; lb, kern, gamma) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "True model")
lines!(ax, x, vec(pred), label = "Fitted model")
axislegend("Method")
f
```
