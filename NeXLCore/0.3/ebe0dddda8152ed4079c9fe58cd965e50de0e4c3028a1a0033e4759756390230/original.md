```
mf2comp(material::String, mfs::UncertainValues)::UncertainValues
mf2comp(mat::Material)::UncertainValues
```

Converts a material composition expressed in the `mfs` UncertainValues struct into a handful of common representations including normalized mass fraction, atomic fraction, mean Z and mean atomic number.  The second form converts a Material into UncertainValues form.
