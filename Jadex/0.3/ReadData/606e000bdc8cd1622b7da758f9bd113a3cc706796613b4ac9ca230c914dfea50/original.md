```
Specie(name::AbstractString; datadir=datadir)
```

Parse the LAMDA collision rate file for an atomic or molecular specie from the filename stem (i.e., without the ".dat" file extension). For example, the stem for the `"hco+@xpol.dat"` file would be `"hco+@xpol"`.
