```
IB_optimize(model::IB; abs_thres = 10^-3, rel_thres = 0.01, ct_thres = 5, n_conv = 1000)
```

Optimizes IB model of the data. Keywords arguments are :     - abs*thres : threshold for convergence in absoulte change of the optimization function (lagrangian) L.     - rel*thres : threshold for convergence in relative change of L.     - ct*thres : number of steps where L has to be < to abs*thres or rel*thres to declare convergence.     - n*conv : limit of the number of iterations for the optimization algorithm.     - scan (bool): when using 'DIB' algorithm, checks and merges clusters if it leads to reduction of cost function.     - report : wether or not to say when and how convergence was reached.
