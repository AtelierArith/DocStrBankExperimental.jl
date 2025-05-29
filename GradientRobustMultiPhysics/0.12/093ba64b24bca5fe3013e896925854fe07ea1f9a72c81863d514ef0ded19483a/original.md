```
FEMatrix{TvM,TiM}(FESX, FESY; name = "auto")
```

Creates FEMatrix with one rectangular block (FESX,FESY) if FESX and FESY are single FESpaces, or a rectangular block matrix with blocks corresponding to the entries of the FESpace vectors FESX and FESY. Optionally a name for the matrix can be given.
