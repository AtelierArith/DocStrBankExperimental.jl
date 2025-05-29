```
pix2zphiNest(res::Resolution, pix) -> (z, phi)
```

Compute the angular coordinates `z = cos(θ), ϕ` of the center of the pixel with number `pix`, assuming the `NEST` numbering scheme for pixels. *Caution:* this method is inaccurate near the poles at high resolutions.
