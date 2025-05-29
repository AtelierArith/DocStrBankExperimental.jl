```
write_dataframes(resultfolder::String, datapath::String; measure::Symbol=:AIC, assemble::Bool=true, fittedparams=Int[])
```

write_dataframes(resultfolder::String,datapath::String;measure::Symbol=:AIC,assemble::Bool=true)

collates run results into a csv file

Arguments

  * `resultfolder`: name of folder with result files
  * `datapath`: name of folder where data is stored
  * `measure`: measure used to assess winner
  * `assemble`: if true then assemble results into summary files
