```
function solar_azimuth_altitude(utc_time, lat, lon, alt)
```

Given a UTC time `utc_time`, latitude `lat`, longitude `lon`, and altitutde `alt`, return the solar azimuth and solar elevation angles (in degrees) relative to that location.

This is a Julia (re)implementation of the Matlab script by Darin C. Koblick [(link)](https://www.mathworks.com/matlabcentral/fileexchange/23051-vectorized-solar-azimuth-and-elevation-estimation).

Other references:

  * [http://stjarnhimlen.se/comp/tutorial.html#5](http://stjarnhimlen.se/comp/tutorial.html#5)
  * [http://www.stargazing.net/kepler/altaz.html](http://www.stargazing.net/kepler/altaz.html)
