```
Species Struct:
```

The Particle struct is used for keeping track  of information specifice to the chosen particle.

## Fields:

1. `name::String': 				the name of the particle
2. `int_charge::typeof(1u"q")': 				 the net charge of the particle in units of |e|

```
																	 	 - bookkeeping only, thus in internal units
																		 - use the 'charge()' function to get the charge 
																		 - in the desired units
```

3. `mass::typeof(1.0u"eV/c^2")': 				 the mass of the particle in eV/c^2

```
																		 - bookkeeping only, thus in internal units
																	 	 - use the 'mass()' function to get the mass 
																		 - in the desired units
```

4. `spin::typeof(1.0u"h_bar")': 					 the spin of the particle in ħ
5. `moment::typeof(1.0u"eV/T")': 					 the magnetic moment of the particle in eV/T
6. `iso::Int': 												 if the particle is an atomic isotope, this is the

```
																		 - mass number, otherwise -1
```

7. `kind::Kind.T': 									 the kind of particle (ATOM, HADRON, LEPTON, PHOTON, NULL)                                     - NULL kind defines a null particle, which is not a real particle                                      - but a placeholder

## Constructors:

This structure has the following constructor

```
Species(speciesname::String)
```

This constructor is used to create a species struct for a subatomic particle or an atomic species by giving the name  of the particle.

Here are some ways to use this constructor:

1. If the particle is To construct a subatomic species, put the name of the subatomic species in the field name.

Note that the name must be provided exactly.

2. If the particle is an atomic species, put the atomic symbol in the name along with isotope and charge information.

      * The name of the atomic species should be in the format:

    "mass number" + "atomic symbol" + "charge" the mass number in front of the atomic symbol, and the charge at the end.

      * The mass number and charge are optional.
      * The mass number can be in unicode superscript or in ASCII, with an optional "#" in front.

    e.g.   Species("¹H") - Hydrogen-1  Species("1H") - Hydrogen-1  Species("#1H") - Hydrogen-1

      * if the mass number is not specified, the most abundant isotope will be used.
      * The charge can be in the following formats:

          * "+" represents single positive charge
          * "++" represents double positive charge
          * "+n" or "n+" represents n positive charge, where n can be unicode superscript
          * "-" represents single negative charge
          * "–-" represents double negative charge
          * "-n" or "n-" represents n negative charge, where n can be unicode superscript

    e.g.   Species("C+") - Carbon with a single positive charge  Species("N³⁻") - Nitrogen with a 3 negative charge

      * if charge is not specified, the charge will be 0.
3. To create a null species, use the name "Null" or "null" or "".
4. To create an anti-particle, prepend "anti-" to the name of the particle. e.g. Species("anti-H") - Anti-hydrogen Species("anti-Fe") - Anti-iron Species("anti-positron") - Positron
