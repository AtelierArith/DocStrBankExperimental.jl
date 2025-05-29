```
write_measurements!(model::Type, data::Dict, pf_results::Dict, path::String; exclude::Vector{String}=String[], σ::Float64=0.005)
```

Function to write a csv file with measurements, to be used to run state estimation calculations. The file is built starting from power flow results from PowerModelsDistribution.jl (or any dictionary with the same format). The measurements consist of voltage and power/current injections in correspondence of all generators and loads. The exact measurement type depends on the chosen power flow formulation, e.g., with the AC Polar formulation, these are voltage magnitude and active and reactive power.

# Arguments

  * `model`: power flow type of the generated measurements, e.g., ACPUPowerModel.            If it does not match the power flow model of the `pf_results`, it might not work.            `pf_results` can be post-processed, e.g., polar results can be converted in rectangular            and viceversa, to make the result dictionary compatible.
  * `data`: MATHEMATICAL data dictionary in a format usable with PowerModelsDistribution
  * `pf_results`: PowerModelsDistribution solution dictionary or similar format
  * `path`: path where the csv file will be generated and stored
  * `exclude`: select quantities from the `pf_results` dictionary to be excluded from the measurement              generation. For example, to ignore generator results with ACPUPowerModel,              set exclude = ["pg", "qg"].
  * `σ`: standard deviation of demand/generation measurements. If a float, their stdev of the relative       bus voltage measurements is taken with `get_sigma()`. If a dictionary (recommended option), the       individual σ of each measurement quantity is declared.
