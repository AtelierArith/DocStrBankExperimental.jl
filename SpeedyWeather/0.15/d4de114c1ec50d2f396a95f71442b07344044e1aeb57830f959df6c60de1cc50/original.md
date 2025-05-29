Simulation is a container struct to be used with `run!(::Simulation)`. It contains

  * `prognostic_variables::SpeedyWeather.PrognosticVariables`: define the current state of the model
  * `diagnostic_variables::SpeedyWeather.DiagnosticVariables`: contain the tendencies and auxiliary arrays to compute them
  * `model::SpeedyWeather.AbstractModel`: all parameters, constant at runtime
