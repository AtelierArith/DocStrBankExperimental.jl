The Scene type defines a function to be used to render a range of frames in a movie.

  * the `movie` created by Movie()
  * the `framefunction` is a function taking two arguments: the scene and the framenumber.
  * the `framerange` determines which frames are processed by the function. Defaults to the entire movie.
  * the optional `easingfunction` can be accessed by the framefunction to vary the transition speed
  * the optional `opts` which is a single argument of an abstract type which can be accessed within the framefunction
