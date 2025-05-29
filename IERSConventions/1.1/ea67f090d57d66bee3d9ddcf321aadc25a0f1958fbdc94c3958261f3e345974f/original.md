```
eop_generate_from_txt(m::IERSModel, inputfile, outputfile)
```

Parse TXT files containing IERS EOP data and extract the relevant information to a dedicated  JSMD `.eop.dat` file. Supported formats are the EOP C04 series and the Rapid Data  prediction (finals).

!!! note
    The `outputfile` name should not include the file extension, which is automatically  added by this function.


!!! note
    Depending on the type of file, either the CIP or the nutation corrections may be present.  This function applies a conversion algorithm to automatically retrieve the missing data.


!!! warning
    This routine recognises the file structure and column ordering by analysing the  input file name, which should be left equal to the one retrieved from the IERS website.


### References

  * [USNO finals](https://maia.usno.navy.mil/ser7/readme.finals)
  * [USNO finals 2000A](https://maia.usno.navy.mil/ser7/readme.finals2000A)

### See also

See also [`eop_generate_from_csv`](@ref). 
