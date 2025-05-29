```
get_beam_centre(incif::CifContainer,scan_id,frame_no)
```

Return the beam centre coordinates for `frame_no` of `scan_id`, taking into account all axis positions. Return pixel coordinates slow, fast, and mm coordinates slow, fast as 4 values. The mm coordinates are from the centre of the origin pixel, not the origin of the detector coordinates.
