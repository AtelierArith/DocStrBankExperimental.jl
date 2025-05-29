```
SeisBinHeaders(in,out; <keyword arguments>)
```

Sequentially bin seismic headers using the available grid information.

Keyword arguments should be consistent with SeisGeometry keyword arguments.

# Arguments

  * `in`: filename of input, irregularly sampled data
  * `out`: filename of output, regularly sampled data

# Keyword arguments

  * `style="sxsygxgy"`: bin style. Options: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `ang=90`: inline direction measured in degrees CC from East
  * `gamma=1`: vp/vs ratio for PS Asymptotic Conversion Point gathers (use gamma=1 for PP data)
  * `osx=0`,`osy=0`,`ogx=0`,`ogy=0` : origin for source and receiver coordinate system
  * `omx=0`,`omy=0`,`ohx=0`,`ohy=0`: origin for midpoint and offset coordinate system
  * `oaz=0`,`oh=0` : origin for azimuth and offset coordinate system
  * `dsx=1`,`dsy=1`,`dgx=1`,`dgy=1`: source and receiver step-size
  * `dmx=1`,`dmy=1`,`dhx=1`,`dhy=1`: midpoint and offset step-size
  * `dh=1`,`daz=1`: offset and azimuth step-size
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: grid extreme values for sources
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: grid extreme values for receivers
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: grid extreme values for midpoints
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: grid extreme values for offsets
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: grid extreme values for azimuth and offset
  * `ntrace=10000`: maximum number of traces processed at a time

# Output

In file `out@headers@`, binned headers are saved.

*Credits: Aaron Stanton,2017*
