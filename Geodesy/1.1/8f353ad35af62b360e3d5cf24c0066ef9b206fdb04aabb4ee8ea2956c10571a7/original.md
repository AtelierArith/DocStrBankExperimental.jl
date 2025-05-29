```
WebMercatorfromLLA(datum=wgs84)
```

Convert from LLA to Web Mercator / Pseudo Mercator, following the convention of proj, which uses a scaling factor of the semi-major axis of the ellipsoid https://proj.org/operations/projections/webmerc.html.

!!! warning
    For web mapping applications this projection is ubiquitous due to its simplicity of implementation, but this simplicity gives rise to poor mathematical properties: it doesn't preserve angles away from the equator. Other projections should be preferred if possible, and especially when measurement is important. See https://earth-info.nga.mil/GandG/wgs84/web*mercator/(U)%20NGA*SIG*0011*1.0.0_WEBMERC.pdf for an extended discussion.

