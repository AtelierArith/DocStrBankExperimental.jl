Output of the expfit function. Structure containing information about multiexponential fits.

The fields are as follows:

  * `seq`: The pulse sequence
  * `x` : The x acquisition values (e.g. time for relaxation or b-factor for diffusion).
  * `y` : The y acquisition values.
  * `xfit` : An array with fitted x values (for plotting purposes).
  * `yfit` : An array with fitted y values (for plotting purposes).
  * `u` : The fitted parameters for the `mexp` function.
  * `u0` : The initial parameters for the `mexp` function.
  * `r` : The residuals.
  * `eq` : The equation of the fitted function.
  * `eqn` : The equation of the initial function.
  * `title` : A title describing the data.
