A function to calculate the mixture diffusion coefficients given the binary diffusion coefficients and the mole fractions

# Usage:

D*km!(Dkm, D*ij, molefracs, molwt )

  * Dkm : Array to store the mixture diffusion coefficients (size N)
  * D_ij : N X N Matrix of binary diffusion coefficients
  * molefracs : Mole fractions
  * molwt : species molecular weights
