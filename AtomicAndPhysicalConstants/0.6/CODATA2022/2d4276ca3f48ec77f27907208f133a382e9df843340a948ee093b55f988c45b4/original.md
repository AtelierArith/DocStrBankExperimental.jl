```
	full_name(species::Species)
```

get the full name of a tracked species:

  * if species is subatomic, gives the name in the SUBATOMIC_SPECIES dictionary
  * if species is atomic, gives "mass number" * "atomic symbol" * "charge state",  *e.g.* #3He-1 for a Helion with 3 bound electrons
