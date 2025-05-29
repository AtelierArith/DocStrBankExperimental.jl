```
Batch(dt::AbstractDataTable; 
    signal = :area, 
    rel_sig = :relative_signal, 
    est_conc = :estimated_concentration, 
    true_conc = :true_concentration, 
    acc = :accuracy, 
    calid = r"Cal_(\d)_(\d*-*\d*)", 
    order = "LR", 
    ratio = nothing, 
    df = nothing, 
    f2c = 1,
    parse_decimal = x -> replace(x, "-" => "."))
```

Construct a batch from data. All analytes are considered as normal analytes, so calibration curves are not contructed immediately; call `init_calibration!` after confirming isd and calibration settings in `batch.method.analytetable`.

# Arguments

  * `dt`: data containing both calibration curves and samples.

# Keyword Arguments

  * `signal`: type and key name of experimental acquisition data, e.g. `:area`.
  * `rel_sig`: key name of relative signal.
  * `est_conc`: key name of estimated concentration.
  * `true_conc`: key name of true concentration.
  * `acc`: key name of accuracy.
  * `calid`: identifier for calibration point. It has two possible values.

      * `Regex`, level and concentration related factors (ratio of concentration or dilution factor) should be captured. The former should be able to be parsed as integer directly; the latter should be able to be parsed as floating number after applying `parse_decimal`.
      * `Vector`, assign each sample with number (calibration level), `missing` or `nothing` (normal samples).
  * `order`: `String`, represents the order and identity of captured string; `L` is level, `R` is ratio of concentration, `D` is dilution factor (df).
  * `ratio`: ratio of concantrations of each level. `nothing` indicates using captured values.
  * `df`: dilution factors of each level. `nothing` indicates using captured values.
  * `f2c`: `Number` or vector of numbers; concentration equals to f2c * ratio or f2c / df. When a vector is provided, each element represents `f2c` value of each analyte.
  * `parse_decimal`: `Function`, converts a string into another string which can be parsed as floating number.
