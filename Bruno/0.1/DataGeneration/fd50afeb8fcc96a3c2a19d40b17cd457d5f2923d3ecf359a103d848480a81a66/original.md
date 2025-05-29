```
LogDiffInput(nTimeStep, initial, volatility, drift)
LogDiffInput(;kwargs...)
```

Contains parameters that are used by `makedata()` to synthesize data from a log-normal diffusion process of the form.

$$
P_{t+1} = P_t \cdot e^{drift + volatility \cdot v}
$$

Where P_t is the value of the data at timestep t. The drift and  volatility represent the mean and standard deviation of a normal  distribution. The equation given above expresses them as such by  letting v be a draw from a standard normal distribution which is  then shifted and scaled by the drift and volatility terms.

## Arguments

  * `nTimeStep`:  The number of time steps to synthesize.
  * `initial`:  The assumed value at the 0th time step. Default: 100.
  * `volatility`:  The price volatility as a standard deviation in terms of implied time period. Defaults to 0.3.
  * `drift`: The drift parameter describes the mean of the log-normal diffusion process

given in terms of the entire implied time period (if simulating a year, drift would be annual  expected return). Defaults to 0.02.

## Example

```julia
input1 = LogDiffInput(250, 100, .05, .1)

# initialize first input with default values
input2 = LogDiffInput(250)

# initialize a second input with zero volatility
kwargs = Dict(:nTimeStep=>250, :initial=>100, :volatility=>.05, :drift=>.1)
input3 = LogDiffInput(;kwargs...)
```
