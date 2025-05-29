```
taylorwin(L::IT, nbar = 4, sll = -30) where {IT<:Integer}
```

TAYLORWIN   Taylor window.

TAYLORWIN(N) returns an N-point Taylor window in a column vector.

TAYLORWIN(N,nbar) returns an N-point Taylor window with nbar nearly constant-level sidelobes adjacent to the mainlobe. nbar must be an integer greater than or equal to one.

TAYLORWIN(N,nbar,sll) returns an N-point Taylor window with sll maximum sidelobe level in dB relative to the mainlobe peak. sll must be a negative value, e.g., -30 dB.

nbar should satisfy nbar >= 2*A^2+0.5, where A is equal to acosh(10^(-sll/20))/pi, otherwise the sidelobe level specified is not guaranteed. If nbar is not specified it defaults to 4. sll defaults to -30 dB if not specified.

EXAMPLE This example generates a 64-point Taylor window with 4 sidelobes adjacent to the mainlobe that are nearly constant-level, and a peak sidelobe level of -35 dB relative to the mainlobe peak.

w = taylorwin(64,5,-35); wvtool(w);

See also CHEBWIN.

Copyright 2005-2018 The MathWorks, Inc.

References:     [1] Carrara, Walter G., Ronald M. Majewski, and Ron S. Goodman,         Spotlight Synthetic Aperture Radar: Signal Processing Algorithms,         Artech House, October 1, 1995.     [2] Brookner, Eli, Practical Phased Array Antenna Systems,         Artech House, Inc., 1991, pg. 2-51.
