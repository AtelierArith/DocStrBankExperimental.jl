```
eop_generate_from_csv(m::IERSModel, inputfile, outputfile)
```

Parse CSV files containing IERS EOP data and extract the relevant information to a dedicated  JSMD `.eop.dat` file. Supported formats are the EOP C04 series and the Rapid Data  prediction (finals).

!!! note
    The `outputfile` name should not include the file extension, which is automatically  added by this function.


!!! note
    Depending on the type of file, either the CIP or the nutation corrections may be present.  This function applies a conversion algorithm to automatically retrieve the missing data.


!!! warning
    The rapid data prediction files store the LOD, CIP and nutation corrections in  milliseconds and milliarcseconds, respectively, whereas the EOP C04 files do not. This  routine automatically detects the correct unit of measure by analysing the format of the  input filename. Thus, the filename should be kept equal to the one released by the IERS.


### References

  * [USNO finals](https://maia.usno.navy.mil/ser7/readme.finals)
  * [USNO finals 2000A](https://maia.usno.navy.mil/ser7/readme.finals2000A)

### See also

See also [`eop_generate_from_txt`](@ref). 
