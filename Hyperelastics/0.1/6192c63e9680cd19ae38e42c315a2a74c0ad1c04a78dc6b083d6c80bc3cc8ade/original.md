```julia
FullNetwork(; ℒinv)

```

# Model:

$$
W = (1-\rho)W_{3Chain}+\rho W_{8chain}
$$

# Arguments:

  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used

# Parameters:

  * `μ`
  * `N`
  * `ρ`

> Treloar LR, Riding G. A non-Gaussian theory for rubber in biaxial strain. I. Mechanical properties. Proceedings of the Royal Society of London. A. Mathematical and Physical Sciences. 1979 Dec 31;369(1737):261-80. Wu PD, van der Giessen E. On improved 3-D non-Gaussian network models for rubber elasticity. Mechanics research communications. 1992 Sep 1;19(5):427-33. Wu PD, Van Der Giessen E. On improved network models for rubber elasticity and their applications to orientation hardening in glassy polymers. Journal of the Mechanics and Physics of Solids. 1993 Mar 1;41(3):427-56.

