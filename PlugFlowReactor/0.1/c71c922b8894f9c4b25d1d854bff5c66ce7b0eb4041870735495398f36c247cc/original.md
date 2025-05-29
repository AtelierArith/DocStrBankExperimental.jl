A function for call from other packages, mainly intended for reactor network modeling 

# Method-3

plug(inlet*comp, T, p, vel, l; chem, thermo*obj, md, geometry)

  * inlet*comp : Dictionary of species name and mole fractions. In the case of gasphase chemistry the inlet*comp

may only contain species that are present at the inlet 

  * T : Temperature in K
  * p : Pressure in Pa
  * vel : inlet velocity in m/s
  * l : length of the reactor in m
  * chem: Chemistry to be invoked: tuple Chemistry(surfchem, , true, user_defined)
  * thermo_obj : Thermo Object
  * md : Mechanism definition(Please refer SurfaceReactions.jl and Ga
  * geometry : tuple of reactor geometry (dia,cat_geom)      

      * dia: reactor diameter
      * cat_geom : enhancement factor for the reaction rate due to the catalyst geometry effect
