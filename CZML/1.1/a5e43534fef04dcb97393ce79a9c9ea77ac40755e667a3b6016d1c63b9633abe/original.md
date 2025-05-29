# NearFarScalar

A numeric value which will be linearly interpolated between two values based on an object's distance from the camera, in eye coordinates. The computed value will interpolate between the near value and the far value while the camera distance falls between the near distance and the far distance, and will be clamped to the near or far value while the distance is less than the near distance or greater than the far distance, respectively.

See here for more details: https://github.com/AnalyticalGraphicsInc/czml-writer/wiki/NearFarScalar
