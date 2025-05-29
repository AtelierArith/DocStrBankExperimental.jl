```
getEBV(model::MME,traiti)
```

(internal function) Get breeding values for individuals defined by outputEBV(), defaulting to all genotyped individuals. This function is used inside MCMC functions for one MCMC samples from posterior distributions. e.g., non-NNBayes*partial (multi-classs Bayes) : y1=M1*α1[1]+M2*α2[1]+M3*α3[1]                                            y2=M1*α1[2]+M2*α2[2]+M3*α3[2]; NNBayes*partial:     y1=M1*α1[1]                      y2=M2*α2[1]                      y3=M3*α3[1];
