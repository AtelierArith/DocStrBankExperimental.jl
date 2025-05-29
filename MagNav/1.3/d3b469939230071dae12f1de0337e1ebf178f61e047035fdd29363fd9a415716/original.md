```
sgl_2021_train(f::Union{String,Symbol} = "")
```

Flight data from the 2021 SGL flight data collection - training portion. Collected from 13-Dec-2021 to 05-Jan-2022 near Ottawa, Ontario, Canada by Sander Geophysics Ltd. (SGL) using a Cessna Grand Caravan. Contains:

  * `Flt2001_train.h5`
  * `Flt2002_train.h5`
  * `Flt2004_train.h5`
  * `Flt2005_train.h5`
  * `Flt2006_train.h5`
  * `Flt2007_train.h5`
  * `Flt2008_train.h5`
  * `Flt2015_train.h5`
  * `Flt2016_train.h5`
  * `Flt2017_train.h5`

**Arguments:**

  * `f`: (optional) name of data file (`_train` & `.h5` extension optional)

**Returns:**

  * `p`: path of folder or `f` data file
