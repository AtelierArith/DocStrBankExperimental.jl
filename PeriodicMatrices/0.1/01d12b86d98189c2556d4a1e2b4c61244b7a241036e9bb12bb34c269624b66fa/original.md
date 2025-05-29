```
pmderiv(A::PeriodicFunctionMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false) 
pmderiv(A::PeriodicTimeSeriesMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false) 
pmderiv(A::PeriodicSwitchingMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false)
```

Compute the derivative of a continuous-time periodic matrix using finite difference formulas. By default `method = "cd"`, in which case  the central difference formula is used for approximating the derivative.  If `method = "4d"`, a fourth order finite difference formula is used for higher accuracy. If `method = ""`, the forward difference formula is used if the  time difference `h` is missing or `h > 0`, and a backward difference formula is used if `h < 0`. If `discont = true`, then initial discountinuities at `t = 0` and  terminal discountinuities at `tsub := A.period/A.nperiod` (the subperiod) are  avoided by using the forward or backward differentiation formulas at `t =  0` and at `t = tsub`, respectively.  This approach generally leads to lower accuracy estimations at `t = 0` and `t = tsub`.   

*Note:* To allow the application of the finite difference approximations to periodic matrices of types `PeriodicTimeSeriesMatrix` and `PeriodicSwitchingMatrix`,  these are converted to `PeriodicFunctionMatrix` type. Due to inherent discountinuities of these representations, the accuracy of derivate estimations is usualy poor. To increase the accuracy, it is recommended to perform these conversions before calling the `pmderiv` function, by employing splines based interpolation formulas,  as provided by the function [`ts2pfm`](@ref).  
