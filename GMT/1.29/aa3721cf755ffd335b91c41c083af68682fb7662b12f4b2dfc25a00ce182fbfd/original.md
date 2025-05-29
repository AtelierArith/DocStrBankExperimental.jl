I = mosaic(GI::Union{GMTgrid, GMTimage}; ...)

Same as above but the `lon` & `lat` are extracted from the `GI` header. The grid or image `GI` must have set a valid projection, and it doesn't need to be in geographic coordinates. Coordinates in other reference systems will be converted to geogs.
