```julia
export_results(
    results::PowerSimulations.SimulationResults,
    exports
)

```

Export results to files in the results directory.

# Arguments

  * `results::SimulationResults`: simulation results
  * `exports`: SimulationResultsExport or anything that can be passed to its constructor. (such as Dict or path to JSON file)

An example JSON file demonstrating possible options is below. Note that `start_time`, `end_time`, `path`, and `format` are optional.

```
{
  "decision_models": [
    {
      "name": "ED",
      "variables": [
        "P__ThermalStandard",
      ],
      "parameters": [
        "all"
      ]
    },
    {
      "name": "UC",
      "variables": [
        "On__ThermalStandard"
      ],
      "parameters": [
        "all"
      ],
      "duals": [
        "all"
      ]
    }
  ],
  "start_time": "2020-01-01T04:00:00",
  "end_time": null,
  "path": null,
  "format": "csv"
}

```
