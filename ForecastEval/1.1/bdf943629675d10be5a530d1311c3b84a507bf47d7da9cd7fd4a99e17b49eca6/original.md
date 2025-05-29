```
dm(lossdiff::Vector{<:Number}, dmmethod ; kwargs...)
```

This function implements the test proposed in Diebold, Mariano (1995) "Comparing Predictive Accuracy". 

Let x*1 denote forecast 1, x*2 denote forecast 2, and let y denote the forecast target. Let L(., .) denote a loss function. Then the first argument lossdiff is assumed to be a vector created by the following operation: 

L(x*1, y) - L(x*2, y) 

The second argument, dmmethod, can be an explicit method type, currently DMHAC or DMBoot, (see ?DMHAC and ?DMBoot for more detail), in which case the keyword arguments are not needed. 

Alternatively, dmmethod can be set to the Symbol :hac or :boot, depending on whether the user wants to use the HAC method or the bootstrap method. In this instance, the keyword arguments provided will be passed on to DMHAC or DMBoot constructors (see ?DMHAC and ?DMBoot for more detail). 

Finally, the second argument can be omitted entirely, in which case the method will default to the default bootstrap method, which is the stationary bootstrap of Politis and Romano (1993) with block length estimated followed Patton, Politis, and White (2009). 

The output of a Diebold-Mariano test is of type DMTest. Use ?DMTest for more information.
