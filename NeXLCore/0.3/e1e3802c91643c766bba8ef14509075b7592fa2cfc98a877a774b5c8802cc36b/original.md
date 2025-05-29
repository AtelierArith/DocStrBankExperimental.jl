```
atoms_per_cm³(mat::Material, elm::Element) =
```

Number of atoms per cm³ of the specified Element in the specified Material.  The Material must define the `:Density` property.

```
atoms_per_cm³(mat::Material)
```

Total number of atoms per cm³ for all elements in mat. 
