```
sgl_2020_train(f::Union{String,Symbol} = "")
```

Flight data from the 2020 SGL flight data collection - training portion. Collected from 20-Jun-2020 to 07-Jul-2020 near Ottawa, Ontario, Canada by Sander Geophysics Ltd. (SGL) using a Cessna Grand Caravan. Contains:

  * `Flt1002_train.h5`
  * `Flt1003_train.h5`
  * `Flt1004_train.h5`
  * `Flt1005_train.h5`
  * `Flt1006_train.h5`
  * `Flt1007_train.h5`

**Arguments:**

  * `f`: (optional) name of data file (`_train` & `.h5` extension optional)

**Returns:**

  * `p`: path of folder or `f` data file
