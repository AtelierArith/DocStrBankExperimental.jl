```
time2pointing!(sstr::ScanningStrategy, time_s, beam_dir, polangle_rad, resultvec)
time2pointing(sstr::ScanningStrategy, time_s, beam_dir, polangle_rad)
```

Calculate the pointing direction of a beam along the direction `beam_dir`, with a detector sensitive to the polarization along the angle `polangle_rad`. The result is saved in `resultvec` for `time2pointing!`, and it is the return value of `time2pointing`; it is a 6-element array containing the following fields:

1. The colatitude (in radians) of the point in the sky
2. The longitude (in radians) of the point in the sky
3. The polarization angle, in the reference frame of the sky
4. The X component of the normalized pointing vector
5. The Y component
6. The Z component

Fields #4, #5, #6 are redundant, as they can be derived from the colatitude (field #1) and longitude (field #2). They are returned as the code already computes them.

The vector `beam_dir` and the angle `polangle_rad` must be expressed in the reference system of the focal plane. If `polangle_rad == 0`, the detector measures polarization along the x axis of the focal plane. The normal direction to the focal plane is along the z axis; thus, the boresight director is such that `beam_dir = [0., 0., 1.]`.
