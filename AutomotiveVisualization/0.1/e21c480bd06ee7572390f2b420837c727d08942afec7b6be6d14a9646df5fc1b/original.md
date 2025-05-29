Add an instruction to the rendermodel

INPUT:     rendermodel   - the RenderModel we are adding the instruction to     f             - the function to be called, the first argument must be a CairoContext     args          - tuple of input arguments to f, skipping the CairoContext     coordinate*system - in which coordinate system are the coordinates given (one of :scene, :camera*pixels, :camera*relative)       `:scene` - coordinates are physical coordinates in the world frame in unit [meters]       `:camera*pixels`- coordinates are in pixels and relative to the rectangle selected by the camera in unit [pixels]`:camera_relative` - coordinates are in percentages in the range 0 to 1 of the rectangle selected by the camera

ex: add*instruction!(rendermodel, render*text, ("hello world", 10, 20, 15, [1.0,1.0,1.0]))
