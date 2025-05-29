```julia
export_results(
    results::PowerSimulations.SimulationResults,
    exports
)

```

結果を結果ディレクトリのファイルにエクスポートします。

# 引数

  * `results::SimulationResults`: シミュレーション結果
  * `exports`: SimulationResultsExport またはそのコンストラクタに渡すことができるもの（Dict や JSON ファイルへのパスなど）

可能なオプションを示す例の JSON ファイルは以下の通りです。`start_time`、`end_time`、`path`、および `format` はオプションであることに注意してください。

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
