```
qrm_golub_riley!(shifted_spmat, spfct, x, b, Δx, y; α = ϵm, max_iter = 50, tol = ϵm, transp = 'n')
```

This method implements the Golub-Riley iteration. Given a (possibly ill-conditionned or rank deficient) system `Ax = b` where `A` can have any shape `m×n`, compute `x = A†b = Aᵀ(AAᵀ)†b` where `A†` is the Moore-Penrose pseudoinverse of `A`.

### Input Arguments :

  * `shifted_spmat`: a `qrm_shifted_spmat` type representing the matrix `(A  √α)` where `α` is a regularization parameter for the Golub-Riley iteration. See `qrm_shift_spmat` for more information.
  * `spfct`: a sparse factorization object of type `qrm_spfct`.
  * `x`: the approximate solution vector x := A†b = Aᵀy, the size of this vector is n+m, its values are overwritten by this function and it can be uninitialized when the function is called.
  * `b`: the RHS vector of the linear system, the size of this vector is m.
  * `Δx`: an auxiliary vector used to compute the solution, the size of this vector is n+m and can be uninitialized when the function is called.
  * `y`: the vector used to compute y := (AAᵀ)†b, the size of this vector is n and can be uninitialized when the function is called.
  * `Δy`: an auxiliary vector used to compute the solution, the size of this vector is n and can be uninitialized when the function is called.

The definition of the `shifted_spmat` may look odd at first sight. We use such a block matrix as an argument of `qrm_golub_riley!` because the QR factorization of this matrix has the property that `RᵀR = AᵀA + αI` which is the system we need to repeatedly solve from for the Golub-Riley iteration. 

The Golub-Riley method works as follows:

  * Given A and b, choose a fixed regularization parameter `α > 0` and let x := 0.
  * At each iteration, compute Δx := Aᵀ(AAᵀ + αI)⁻¹ (b - Ax), and update x := x + Δx.

This method has the advantage of only costing one QR-factorization of the `qrm_shifted_spmat` matrix. For more details, see  A. Dax and L. Eldén, Approximating minimum norm solutions of rank-deficient least squares problems, Numerical Linear Algebra with Applications, 5, pp. 79-99, 1998, DOI 10.1002/(SICI)1099-1506(199803/04)5:2<79::AID-NLA126>3.0.CO;2-4
