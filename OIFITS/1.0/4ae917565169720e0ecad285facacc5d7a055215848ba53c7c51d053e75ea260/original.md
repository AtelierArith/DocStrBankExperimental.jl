`OIDataSet` objects store the contents of an OI-FITS file. All data-blocks containing measurements (`OI_VIS`, `OI_VIS2`, `OI_T3`, `OI_FLUX`, and `OI_INSPOL`) are stored into a vector and thus indexed by an integer. Named data-blocks (`OI_ARRAY`, `OI_WAVELENGTH`, and `OI_CORR`) are indexed by their names (converted to upper case letters, with leading and trailing spaces stripped, multiple spaces replaced by a single ordinary space).

Reading an OI-FITS file is as simple as one of:

```
data = OIDataSet(filename)
data = read(OIDataSet, filename)
```

with `filename` the name of the file. Keyword `hack_revn` can be used to force the revision number (FITS keyword `OI-REVN`) of all OI-FITS data-blocks; `hack_revn` may be set to an integer, the revision number to assume for all data-blocks, or to a function that takes 2 arguments, the type and actual revision number of the current data-block, and that returns the revision number to assume. For example, to force revision number 1 for all `OI_VIS` data-blocks and left others unchanged:

```
data = OIDataSet(filename; hack_revn = (T, revn) -> (T === OI_VIS ? 1 : revn))
```

Looping over `OI_VIS` data-blocks in the data-set can be done as follows:

```
for db in data.vis
    ...
end
```

and similarly for fields `vis2`, `t3`, `flux`, and `inspol` to access `OI_VIS2`, `OI_T3`, `OI_FLUX`, and `OI_INSPOL` data-blocks.

The data-set has a number of other public properties:

```
data.target           # the OI_TARGET data-block
data.instr[insname]   # the OI_WAVELENGTH data-block named `insname`
data.array[arrname]   # the OI_ARRAY data-block named `arrname`
data.correl[corrname] # the OI_CORR data-block named `corrname`
```
