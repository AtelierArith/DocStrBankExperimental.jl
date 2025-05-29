```julia
ZRDAAM(
    DzD0::T = 193188.0          # [cm^2/sec] Maximum diffusivity, crystalline endmember
    DzD0_logsigma::T=log(2)/2   # [unitless] log uncertainty (default = log(2)/2 = a factor of 2 two-sigma)
    DzEa::T=165.0               # [kJ/mol] Activation energy, crystalline endmember
    DzEa_logsigma::T=log(2)/4   # [unitless] log uncertainty (default = log(2)/4 = a factor of sqrt(2) two-sigma)
    DN17D0::T = 6.367E-3        # [cm^2/sec] Maximum diffusivity, amorphous endmember
    DN17D0_logsigma::T=log(2)/2 # [unitless] log uncertainty (default = log(2)/2 = a factor of 2 two-sigma)
    DN17Ea::T=71.0              # [kJ/mol] Activation energy, amorphous endmember
    DN17Ea_logsigma::T=log(2)/4 # [unitless] log uncertainty (default = log(2)/4 = a factor of sqrt(2) two-sigma)
    lint0::T=45920.0            # [nm]
    SV::T=1.669                 # [1/nm]
    Bα::T=5.48E-19              # Amorphous material produced per alpha decay [g/alpha]
    Phi::T=3.0                  # unitless
    beta::T=-0.05721            # Zircon anealing parameter
    C0::T=6.24534               # Zircon anealing parameter
    C1::T=-0.11977              # Zircon anealing parameter
    C2::T=-314.937 - LOG_SEC_MYR # Zircon anealing parameter. Includes conversion factor from seconds to Myr for dt (for performance), in addition to traditional C2 value
    C3::T=-14.2868              # Zircon anealing parameter
    rmin::T=0.2                 # Damage conversion parameter
    rmin_sigma::T=0.15          # Damage conversion parameter uncertainty
)
```

Zircon Radiation Damage Accumulation and Annealing Model (ZRDAAM) of Guenthner et al. 2013 (doi: 10.2475/03.2013.01)
