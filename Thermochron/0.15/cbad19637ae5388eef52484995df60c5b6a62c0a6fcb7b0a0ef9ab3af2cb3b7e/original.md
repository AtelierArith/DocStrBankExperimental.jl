```julia
RDAAM(
    D0L::T=0.6071               # [cm^2/sec] Maximum diffusivity
    D0L_logsigma::T=log(2)/2    # [unitless] log uncertainty (default = log(2)/2 = a factor of 2 two-sigma)
    EaL::T=122.3                # [kJ/mol] Activation energy
    EaL_logsigma::T=log(2)/4    # [unitless] log uncertainty (default = log(2)/4 = a factor of sqrt(2) two-sigma)
    EaTrap::T=34.0              # [kJ/mol] Activation energy
    EaTrap_logsigma::T=log(2)/4 # [unitless] log uncertainty (default = log(2)/4 = a factor of sqrt(2) two-sigma)
    psi::T=1e-13                # empirical polynomial coefficient
    omega::T=1e-22              # empirical polynomial coefficient
    etaq::T=0.91                # Durango ηq
    rhoap::T=3.19               # Density of apatite [g/cm3]
    L::T=0.000815               # Etchable fission track half-length, cm
    lambdaf::T=8.46e-17         # 
    lambdaD::T=1.55125e-10      # 
    beta::T=0.04672             # Apatite annealing parameter. Also caled alpha, but equivalent to beta in ZRDAAM
    C0::T=0.39528               # Apatite annealing parameter
    C1::T=0.01073               # Apatite annealing parameter
    C2::T=-65.12969 - LOG_SEC_MYR # Apatite annealing parameter. Includes conversion factor from seconds to Myr for dt, in addition to traditional C2 value
    C3::T=-7.91715              # Apatite annealing parameter
    rmr0::T=0.83                # Damage conversion parameter
    rmr0_sigma::T=0.15          # Damage conversion parameter uncertainty
    kappa::T=1.04-0.83          # Damage conversion parameter
    kappa_rmr0::T=1.04          # Damage conversion parameter (the sum of kappa and rmr0)
)
```

Apatite Radiation Damage Accumulation and Annealing Model (RDAAM) of Flowers et al. 2009 (doi: 10.1016/j.gca.2009.01.015)
