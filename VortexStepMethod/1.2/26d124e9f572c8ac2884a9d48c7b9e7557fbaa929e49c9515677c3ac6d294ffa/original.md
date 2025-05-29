```
init!(body_aero::BodyAerodynamics; init_aero, va, omega)
```

Initialize a BodyAerodynamics struct in-place by setting up panels and coefficients.

# Arguments

  * `body_aero::BodyAerodynamics`: The structure to initialize

# Keyword Arguments

  * `init_aero::Bool`: Wether to initialize the aero data or not
  * `va=[15.0, 0.0, 0.0]`: Apparent wind vector
  * `omega=zeros(3)`: Turn rate in kite body frame x y and z

# Returns

nothing
