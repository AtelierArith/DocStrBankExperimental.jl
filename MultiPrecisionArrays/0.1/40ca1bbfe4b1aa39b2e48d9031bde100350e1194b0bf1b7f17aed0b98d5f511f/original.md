mplu!(MPA::MPArray; residterm=residtermdefault)

Plain vanilla MPArray factorization: Factor the low precision copy and leave the high precision matrix alone. You get a factorization object as output and can use `\` to solve linear systems.

The story on interprecision transfers is that you can set the Boolean `onthefly` when you construct the MPArray. If you use `mplu` then you get the defaults

  * If `onthefly == false` then the solver downcasts the residual

before the solve and avoids N^2 interprecision transfers.

  * If `onthefly == true` then the solver does interprecision transfers  on the fly and incurs the N^2 interprecision transfer cost for that. 

    `onthefly == true` is what you must use if you plan to use  the low precision  factorization as a preconditioner in IR-GMRES or you're working in  Float16 and the matrix is very ill-conditioned. 

    `onthefly == nothing` means you take the defaults.

The kwarg `residterm` sets the termination criterion.  `residterm == true` (default) terminates the iteration on  small residuals.  `residterm == false` terminates the iteration on small normwise backward errors. Look at the docs for details.

If you want to use static arrays with this stuff, use the  mutable @MArray constructor
