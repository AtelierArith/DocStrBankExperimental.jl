```
makeDCWs(fname; float=false, name_cdl="xxxx.cdl", name_nc="", compress=true,
         attrib="", fix_RU::Bool=false, deltmp=true)
```

Convert the contents of the OGR file `fname` into a NetCDF CDL or NC file with the structure of the GMT DCW format. So far, only administrative level 0 polygons (the country borders) are supported.

### Parameters

  * `fname`: The name of the file to be converted. It needs to be an OGR readable file with polygons and metadata containing codes in ISO 3166-1 Alpha-3 or Alpha-2. Note: if the file being converted is the "world-administrative-boundaries" from OpenDataSoft (see full link below), it lacks the Anctartica polygons. A trick to get it is to extract the Antractica polygons from a Natural Earth file. Specifically, if a file named "ne*10m*admin*0*countries.shp.zip" exists in the same directory as the one being converted, it will be used to extract the missing Antractica polygons.

### Keywords

  * `attrib`: The name of the attribute field in the OGR file that contains the country codes. It has to be an attribute whose value has to be either a ISO 3166-1 Alpha-3 or Alpha-2 code. For convenience, we provide defaults for 'Natural Earth' https://www.naturalearthdata.com/downloads/10m-cultural-vectors/ files (`attrib="ADM0_A3"`), 'World Administrative Boundaries' https://public.opendatasoft.com/explore/dataset/world-administrative-boundaries/export/ (`attrib="iso3"`) and 'Open Street Maps' (`attrib="iso2"`). For other products, you will need to first load the file with `gmtread` and then check the attributes to find out the attribute name that holds the country codes. Something like: $o = gmtread("the_file"); info(o[1].attrib)$
  * `float`: If true, save the coordinates in float 32 bits. The default is to use a scheme that scales the coordinates to fit in a UInt16 variable. GMT knows how to read both UInt16 and Float32 files.
  * `name_cdl`: The name of the CDL file (default: "xxxx.cdl"). This file gets deleted if `deltmp` = true.
  * `name_nc`: Name of the final netCDF file. WARNING: for this operation to work it is MANDATORY that the executable `ncgen` is in the path.
  * `compress`: If true, compress the nc file with level 9 (default: true). Only used if `name_nc` is not empty and needs that the executable `nccopy` is in the path.
  * `fix_RU`: The Russia polygon is often split at the dateline. If we find this is be true and this option is `true`, then it try to merge the two parts of Siberia in a single big Russia polygon. The default is `false` because probability that this operation goes wrong is not that low. this attempt fails set it to `false` and live with the split polygons.
  * `deltmp`: Delete temporary files (default: true). Only used if `name_nc` is not empty

### Example

```julia
# Create a xxxx.cdl file with data scaled to Uint16 from the ne_10m_admin_0_countries_iso.shp.zip file
makeDCWs("ne_10m_admin_0_countries_iso.shp.zip")

# After that, to create a netCDF file "NE10m.nc" run in the command line:
ncgen -b -k 3 -o NE10m.nc -x xxxx.cdl

# and to compress it with level 9
nccopy -k 3 -d 9 -s NE10m.nc NE10m_9.nc

# To create a compressed netCDF file "NE10m.nc" with data stored in single precision.
makeDCWs("ne_10m_admin_0_countries_iso.shp.zip", name_nc="NE10m_f32.nc", float=true)
```
