`life_run(A)` runs the game of life starting with the matrix `A`. It is visualized on the screen. It will run forever unless:

  * there are no live cells remaining,
  * the current state is the same as the previous state, or
  * the current state is the same as the state two steps earlier.

If `life_run` halts, it returns the number of iterations.

Optional named arguments:

  * `pause=0.0`: number of extra seconds between frames
  * `wrap=false`: determine if the board wraps (is toroidal)
  * `counter=false`: show the step number below the image
  * `max_steps`: maximum number of steps
