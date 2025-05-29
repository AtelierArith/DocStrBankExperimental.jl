# Amplification

Amplification is a time series, therefore it is a function of time

## The relationship is demonstrated by

$$
R = f(t)
$$

$$
f(t) = R_{max}(1-e^{-\alpha(t-t_{eff})^2})
$$

### Variables

  * R: The response is the dependent variable
  * t: Time is the independent variable.

### Parameters

  * ($t_{eff}$): The effective time delay is a short delay between stimulus onset and response onset indicative of the biomolecuar diffusion rates
  * ($\alpha$): The amplification coefficient  represents the rate of the response increases from the biomolecular processes.

### Function usage

[IN 1]:  AMP(t, α, t_eff, rmax)

[OUT 1]: Response
