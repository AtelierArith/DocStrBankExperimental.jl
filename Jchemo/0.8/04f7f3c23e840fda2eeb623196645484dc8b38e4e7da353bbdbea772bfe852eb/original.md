```
selwold(indx, r; smooth = true, npoint = 5, alpha = .05, digits = 3, graph = true, 
    step = 2, xlabel = "Index", ylabel = "Value", title = "Score")
```

Wold's criterion to select dimensionality in LV models (e.g. PLSR).

  * `indx` : A variable representing the model parameter(s), e.g. nb. LVs if PLSR models.
  * `r` : A vector of error rates (n), e.g. RMSECV.

Keyword arguments:

  * `smooth` : Boolean. If `true`,  the selection is done    after a moving-average smoothing of rate R   (see function `mavg`).
  * `npoint` : Window of the moving-average used to    smooth rate R.
  * `alpha` : Proportion alpha used as threshold    for rate R.
  * `digits` : Number of digits in the outputs.
  * `graph` : Boolean. If `true`, outputs are plotted.
  * `step` : Step used for defining the xticks    in the graphs.
  * `xlabel` : Horizontal label for the plots.
  * `ylabel` : Vertical label for the plots.
  * `title` : Title of the left plot.

The slection criterion is the "precision gain ratio": 

  * R = 1 - `r`(a+1) / `r`(a)

where `r` is an observed error rate quantifying the model  performance (e.g. RMSEP, classification error rate, etc.)  and a the model dimensionnality (= nb. LVs). `r` can also represent  other indicators such as the eigenvalues of a PCA.

R is the relative gain in perforamnce efficiency after a new LV  is added to the model. The iterations continue until R becomes lower  than a threshold value `alpha`. By default and only as an indication,  the default `alpha`=.05 is set in the function, but the user should set  any other value depending on his data and parsimony objective.

In his original article, Wold (1978; see also Bro et al. 2008) used  the ratio of cross-validated over training residual sums of squares,  i.e. PRESS over SSR. Instead, function `selwold` compares values of  consistent nature (the successive values in the input vector `r`).  For instance, `r` was set to PRESS values in Li et al. (2002) and  Andries et al. (2011), which is equivalent to the "punish factor"  described in Westad & Martens (2000).

The ratio R can be erratic (particulary when `r` is the error rate  of a discrimination model), making difficult the dimensionnaly  selection. In such a situation, function `selwold` proposes to calculate a smoothing of R (argument `smooth`).

The function returns two outputs (in addition to eventual plots):

  * `opt` : The index corresponding to the minimum value of `r`.
  * `sel` : The index of the selection from the R (or smoothed R)    threshold.

## References

Andries, J.V.M., Vander Heyden, Y., Buydens, L.M.C., 2011. Improved  variable reduction in partial least squares modelling based on  Predictive-Property-Ranked Variables and adaptation of partial least  squares complexity. Analytica Chimica Acta 705, 292-305.  https://doi.org/10.1016/j.aca.2011.06.037

Bro, R., Kjeldahl, K., Smilde, A.K., Kiers, H.A.L., 2008. Cross-validation  of component models: A critical look at current methods. Anal Bioanal Chem  390, 1241-1251. https://doi.org/10.1007/s00216-007-1790-1

Li, B., Morris, J., Martin, E.B., 2002. Model selection for partial least  squares regression. Chemometrics and Intelligent Laboratory Systems 64, 79-89.  https://doi.org/10.1016/S0169-7439(02)00051-5

Westad, F., Martens, H., 2000. Variable Selection in near Infrared Spectroscopy  Based on Significance Testing in Partial Least Squares Regression. J. Near Infrared  Spectrosc., JNIRS 8, 117â124.

Wold S. Cross-Validatory Estimation of the Number of Components in Factor  and Principal Components Models. Technometrics. 1978;20(4):397-405

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
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
n = nro(Xtrain)

segm = segmts(n, 50; rep = 30)
model = plskern()
nlv = 0:20
res = gridcv(model, Xtrain, ytrain; segm, score = rmsep, nlv).res
res[res.y1 .== minimum(res.y1), :]
plotgrid(res.nlv, res.y1;xlabel = "Nb. LVs", ylabel = "RMSEP").f
zres = selwold(res.nlv, res.y1; smooth = true, graph = true) ;
@show zres.opt
@show zres.sel
zres.f
```
