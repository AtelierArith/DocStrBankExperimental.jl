```
soslyapb(s::AbstractSwitchedSystem, d::Integer;
         verbose=0, tol=1e-5, step=0.5, scaling=quickub(s),
         ranktols=tol, disttols=tol, kws...)
```

Find upper bounds to the (constrained) Joint Spectral Radius [(5), PJ08]. Lower bounds a obtained using guarantees in [LPJ19].

[LPJ19] B. Legat, P. A. Parrilo and R. M. Jungers *An entropy-based bound for the computational complexity of a switched system*. IEEE Transactions on Automatic Control, **2019**.

[PJ08] P. Parrilo and A. Jadbabaie. *Approximation of the joint spectral radius using sum of squares*. Linear Algebra and its Applications, Elsevier, **2008**, 428, 2385-2402
