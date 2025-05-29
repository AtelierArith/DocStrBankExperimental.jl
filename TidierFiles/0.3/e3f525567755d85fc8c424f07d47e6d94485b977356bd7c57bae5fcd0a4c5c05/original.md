```
read_json(path::String; null = missing, convertMixedNumberTypes::Bool = true)
```

Read data from a JSON file into a DataFrame

# Arguments

  * `path::String`: A file name or a URL to the JSON file
  * `null`: Determines what data type a JSON null should be
  * `convertMixedNumberTypes::Bool`: When parsing numers in JSON, they can be interpreted as Float64 or Int64, setting this flag to true, means mixed numers (in the same column) will be interpreted as Float64

# Examples

```julia

julia> df = read_json("https://raw.githubusercontent.com/vega/vega-datasets/refs/heads/main/data/movies.json")
3201×16 DataFrame
  Row │ Director         Worldwide Gross  Running Time min  US DVD Sales  Source                        Distributor  ⋯
      │ String?          Int64?           Int64?            Int64?        String?                       String?      ⋯
──────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
    1 │ missing                   146083           missing       missing  missing                       Gramercy     ⋯
    2 │ missing                    10876           missing       missing  missing                       Strand
  ⋮   │        ⋮                ⋮                ⋮               ⋮                     ⋮                        ⋮    ⋱
 3200 │ Martin Campbell        141475336               129       missing  Remake                        Sony Picture
 3201 │ Martin Campbell        233700000               136       missing  Remake                        Sony Picture
```
