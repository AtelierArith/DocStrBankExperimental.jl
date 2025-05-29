# SteamTables

IAPWS-97 Industrial Formulation Properties of water and steam. Provides the Gibbs and Helmholtz free energies, enthalpy, entropy Cp, Cv and sonic velocity given inputs that are eith P&T, P&h or P&s.

## Exported functions:

### Single input:

Psat(T) and Tsat(P) returns the saturation temperature or pressure   SatDensL(T) and SatDensV(T) return the saturated densities   SatHL(T) and SatHV(T) return the saturated enthalpies   SatSL(T) and SatSV(T) return the saturated entropies   DeltaHvap(T) returns the latent heat of vaporisation

### Two inputs:

P and T   SpecificG,    SpecificF,     SpecificV,     SpecificU,      SpecificS,   SpecificH,    SpecificCP,    SpecificCV,    SpeedOfSound

P and h   SpecificG*Ph, SpecificF*Ph,  SpecificV*Ph,  SpecificU*Ph,   SpecificS*Ph,   SpecificH*Ph, SpecificCP*Ph, SpecificCV*Ph, SpeedOfSound*Ph   Quality*Ph, Temperature_Ph

P and s   SpecificG*Ps, SpecificF*Ps,  SpecificV*Ps,  SpecificU*Ps,   SpecificS*Ps,   SpecificH*Ps, SpecificCP*Ps, SpecificCV*Ps, SpeedOfSound*Ps   Quality*Ps, Temperature_Ps

T and h   Quality_Th

T and s   Quality_Ts

SpecificG    [kJ/kg]  Specific Gibbs free energy SpecificF    [kJ/kg]  Specific Helmholtz free energy SpecificV    [m3/kg]  Specific volume SpecificU    [kJ/kg]  Specific internal energy SpecificS    [kJ/kgK] Specific entropy SpecificH    [kJ/kg]  Specific enthalpy SpecificCp   [kJ/kgK] Specific isobaric heat capacity SpecificCv   [kJ/kgK] Specific isochoric heat capacity SpeedOfSound [m/s]    Sonic velocity

By default temperatures in K, pressures in MPa

If units are associated with inputs via Unitful.jl, the return values will also have default units associated with them. These can be converted to preferred units in the calling function.

##Exported constants   R  = 0.461526   [kJ/kg/K] Universal gas constant   Tc = 647.096    [K]       Critical temperature of water   Pc = 22.064     [MPa]     Critical pressure of water   ρc = 322.       [kg/m3]   Critical density of water   T3 = 273.16     [K]       Triple point temperature of water   P3 = 611.657E-6 [MPa]     Triple point pressure of water   Mr = 18.01528   [kg/kmol] Molecular weight of water

Exported constants do not have associated units. Units can be easily added,   e.g.

Ru = R * 1.0u"kJ/kg/K"
