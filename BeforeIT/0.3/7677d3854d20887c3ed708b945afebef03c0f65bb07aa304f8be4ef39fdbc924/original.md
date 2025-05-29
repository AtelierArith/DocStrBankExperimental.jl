This is a Aggregates type. It is used to store the aggregate variables of the economy. Note that `t` is an integer, while the rest are floats or vectors of floats.

# Fields

  * `Y [vector]`: GDP data + predictions
  * `pi_ [vector]`: inflation data + predictions
  * `P_bar`: Global price index
  * `P_bar_g [vector]`: Producer price index for principal good g
  * `P_bar_HH`: Consumer price index
  * `P_bar_CF`: Capital price index
  * `P_bar_h`: CPI_h
  * `P_bar_CF_h`: Capital price index _h
  * `Y_e`: Expected GDP
  * `gamma_e`: Expected growth
  * `pi_e`: Expected inflation
  * `t`: Time index
