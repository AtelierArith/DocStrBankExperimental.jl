```
SeisGeometry(in;<keyword arguments>)
```

Update headers with geometry information. Offsets and azimuths are calculated from source and receivers coordinates.

# Arguments

  * `in`: input filename

# Keyword arguments

  * `ang=90`: inline direction measured in degrees CC from East
  * `gamma=1`: vp/vs ratio for PS Asymptotic Conversion Point gathers (use gamma=1 for PP data)
  * `osx=0`,`osy=0`,`ogx=0`,`ogy=0` : origin for source and receiver coordinate system
  * `omx=0`,`omy=0`,`ohx=0`,`ohy=0`: origin for midpoint and offset coordinate system
  * `oaz=0`,`oh=0` : origin for azimuth and offset coordinate system
  * `dsx=1`,`dsy=1`,`dgx=1`,`dgy=1`: source and receiver step-size
  * `dmx=1`,`dmy=1`,`dhx=1`,`dhy=1`: midpoint and offset step-size
  * `dh=1`,`daz=1`: offset and azimuth step-size

# Outputs

the @headers@ file is updated with the following information:

  * hx,hy,h,az,mx,my : calculated offset, azimuth and midpoint
  * isx,isy,igx,igy,imx,imy,ihx,ihy,ih,iaz: calculated grid nodes for source and receiver position and midpoint, offset and azimuth.

*Credits: A. Stanton, 2017*
