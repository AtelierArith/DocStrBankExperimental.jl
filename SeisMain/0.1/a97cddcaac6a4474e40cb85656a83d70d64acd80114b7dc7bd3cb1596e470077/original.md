```
  SeisPatch(in,out;<keyword arguments>)
```

Creates overlapping 5d patches from a 5d volume

# Arguments

  * `in::String`: input filename (data should have grid information in headers)
  * `out::String`: prefix for output filenames

# Keyword arguments

  * `style="sxsygxgy"`: bin style. Options: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: grid extreme values for sources
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: grid extreme values for receivers
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: grid extreme values for midpoints
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: grid extreme values for offsets
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: grid extreme values for azimuth and offset
  * `it_WL=9e9`,`it_WO=0` : length and overlapping samples in time patches
  * `ix1_WL=9e9`,`ix1_WO=0`:length and overlapping samples in first space dimension
  * `ix2_WL=9e9`,`ix2_WO=0`,`ix3_WL=9e9`,`ix3_WO=0`,`ix4_WL=9e9`,`ix4_WO=0`

# Output

`filename,npatch`: String Array with the file name of the data patches, number of patches created

*Credits: A. Stanton*
