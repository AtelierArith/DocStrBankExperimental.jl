```
solve(prob::SciMLBase.AbstractSteadyStateProblem,
      alg::CTKAlg;
      nrm=norm,
      τstop=1e12*365*24*60*60,
      preprint="",
      maxItNewton=50)
```

Solves `prob` using an AIBECS-customized version of C.T.Kelley Shamanskii-method algorithm.
