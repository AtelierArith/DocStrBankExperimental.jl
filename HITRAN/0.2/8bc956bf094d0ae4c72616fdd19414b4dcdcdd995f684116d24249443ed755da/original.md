```
apply_instrument_function(ν, α[, instrument_function=:rectangular, instrument_wing=10.0, instrument_resolution=0.1])
```

Applies an instrument function to the given input spectrum.

# Arguments

  * `ν`: The wavenumber vector (NOTE: Uniform spacing is assumed but not checked!)
  * `α`: The calculated absorption coefficient using [`α`](@ref)
  * `instrument_function` (optional): A Symbol describing one of the instrument functions below
  * `instrument_wing` (optional): The half-width of the range for calculating the instrument function in $cm^{-1}$
  * `instrument_resolution` (optional): The full-width of the instrument resolution in $cm^{-1}$

# Output

Returns a new vector with the spectrum influenced by the instrument function

# Instrument functions

The following instrument functions $I(x, Δ)$ are supported. Here `x`is the coordinate for evaluating the function, whose range is given by `instrument_wing`. `Δ` is the resolution parameter `instrument_resolution`. Use the stated symbol as value for the argument `instrument_function`.

| Symbol         |                                                                       Equation                                                                       |                                                      Description |
|:-------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------:| ----------------------------------------------------------------:|
| `:rectangular` |                   $\begin{cases} \frac{1}{Δ} & \lvert x \rvert \leq \frac{Δ}{2} \\ 0 & \lvert x \rvert > \frac{Δ}{2} \end{cases}$                    |                                A rectangular instrument function |
| `:triangular`  |             $\begin{cases} \frac{1}{Δ} (1 - \frac{\lvert x \rvert}{Δ}) & \lvert x \rvert \leq Δ \\ 0 & \lvert x \rvert > Δ \end{cases}$              |                                 A triangular instrument function |
| `:gaussian`    |               $\frac{2}{Δ} \sqrt{\frac{\mathrm{ln}2}{\pi}} \mathrm{exp} \left (- \mathrm{ln}2 \left ( \frac{2x}{Δ}\right)^2 \right )$                |         A Gaussian instrument function (e.g. a broadband source) |
| `:lorentzian`  |                                              $\frac{Δ}{2\pi} \frac{1}{x^2+\left(\frac{Δ}{2}\right)^2}$                                               | A Lorentzian instrument function (e.g. a single frequency laser) |
| `:cosine`      | $\begin{cases} \frac{\pi}{4Δ} \cos \left ( \frac {\pi \lvert x \rvert}{2Δ} \right ) & \lvert x \rvert \leq Δ \\ 0 & \lvert x \rvert > Δ \end{cases}$ |                                     A cosine instrument function |
| `:diffraction` |                                            $\frac{1}{Δ} \mathrm{sinc}^2 \left(  \frac{\pi x}{Δ} \right)$                                             |                    A diffraction (sinc-type) instrument function |
| `:michelson`   |                                            $\frac{2}{Δ} \mathrm{sinc} \left(  \frac{2 \pi x}{Δ} \right)$                                             |  A Michelson interferometer-type instrument function (e.g. FTIR) |
