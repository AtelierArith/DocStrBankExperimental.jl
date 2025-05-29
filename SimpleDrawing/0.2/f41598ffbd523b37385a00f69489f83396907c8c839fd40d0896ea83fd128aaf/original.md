`draw_vector` is used to draw vectors (line segments with an arrow at one end). The variations are:

  * `draw_vector(x,y)` draws a vector from the origin to `(x,y)`.
  * `draw_vector(x,y,basex,basey)` draws a vector from `(basex,basey)` to

`(basex+x,basey+y)`.

  * `draw_vector(z)` draws a vector from the origin to the complex value `z`.
  * `draw_vector(z,basez)` draws a vector from the complex location `basez` to

`z+basez`.
