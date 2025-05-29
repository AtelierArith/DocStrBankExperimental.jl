```
expfit(n, seq, x, y; kwargs...)
```

Fit an n-exponential function to the data `x` and `y`. 

The outut is an `expfit_struct` structure.

Arguments:

  * `n` : Integer specifying the number of exponential terms.
  * `seq` : pulse sequence.
  * `x` : acquisition x parameter (time for relaxation or b-factor for diffusion).
  * `y` : acquisition y parameter (magnetization).

Optional arguments:

  * `solver` : Optim solver, default choice is IPNewton().
  * `normalize` : Normalize the data before fitting? (default is true).
  * `L` : An integer specifying which norm of the residuals you want to minimize (default is 2).

The `n` argument can also be a vector of initial parameter guesses,  in which case it also determines the number of exponential terms used. It should be of the form [a1, b1, a2, b2, ...],  where a's are the amplitudes and b's are the parameters inside the exponentials.

The length of the vector in this case must be an even number.

The following examples might help to clarify: 

`expfit([a,b] , CPMG, x, y)` -> mono-exponential fit with initial guess: a * exp.( (1/b) * x) 

`expfit([a,b,c,d] , CPMG, x, y)` -> bi-exponential fit with initial guess: a * exp.( (1/b) * x) + c * exp.((1/d) * x) 

`expfit([a,b,c,d,e,f] , CPMG, x, y)` -> tri-exponential fit with initial guess: a * exp.( (1/b) * x) + c * exp.((1/d) * x) + e * exp.((1/f) * x) 

(where a,b,c,d,e,f are numbers of your choice)

Numbers of parameters beyond tri-exponential can also be used, but it is not recommended.
