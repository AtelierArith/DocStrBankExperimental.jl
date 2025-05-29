A function for call from other packages, mainly intended for reactor network modeling

# Usage

batch*reactor(inlet*comp, T, p, time; Asv=1.0, chem, thermo_obj, md)

  * inlet_comp : A dictionary of species and its mole fractions at the reactor inlet
  * T : operating temperature (K)
  * p : operating pressure (Pa)
  * time : integration time (s)
  * Asv : Surface area to volume ratio (important in the case of surface reactions. 1 in the case of gasphase chemistry)
  * thermo_obj : Species thermo object (Please refer IdealGas package documentation)
  * md : MechanismDefinition (Please refer to ReactionCommons documentation)
