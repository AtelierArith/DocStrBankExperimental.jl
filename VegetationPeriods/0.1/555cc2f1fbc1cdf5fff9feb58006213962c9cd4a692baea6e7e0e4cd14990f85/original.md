Calculate start and end date of vegetation periods based on daily average air temperature and the day of the year (DOY). The sum of day degrees within the vegetation period can be included for convenience.

Common methods for determining the onset and end of thermal vegetation periods are provided, for details see the documentation of each method. Popular choices with regard to forest trees in Germany are `Menzel` and `vonWilpert`. Climate change impact studies at NW-FVA are frequently conducted using `Menzel` with "Picea abies (frueh)" and `NuskeAlbert` for all tree species; with tree species specifics accounted for in subsequent statistical models.

Available methods can be queried with `subtypes(VegetationStartMethod)` and `subtypes(VegetationEndMethod)`

Arguments:

  * `dates`  is a vector of calendar dates (object of class `Date`). Must contain entire years if `est_prev > 0` else the first year may comprise only November and December.
  * `Tavg` is a vector of daily average air temperatures in degree Celsius. Same length as `dates`.
  * `start_method` is a VegetationStartMethod.
  * `end_method` is a VegetationEndMethod.
  * `Tsum_out` is a boolean. Return the sum of daily mean temperatures above  `Tsum_crit` within vegetation period, also known as growing day degrees.
  * `Tsum_crit` threshold for sum of day degrees. Only daily mean temperatures above `Tsum_crit`   will be tallied. The default of `0` prevents negative daily temperatures from reducing the sum.   Climate change studies often use a threshold of `5`.
  * check_data is a boolean. Perform plausibility checks on the temperature data.   Plausible range is -35 to +40°C.

Returns: A `DataFrame` with year, date and DOY of start and end day of the vegetation period for (each) year of the input data.

Example:

```
dates   = Date("2018-01-01"):Day(1):Date("2022-12-31")
Tavg    = 
    30 * (0.3 .+ 1/2*cos.(dayofyear.(dates)/365 * 2π .- π)) .+ 
    rand([-34.9 : 0.1 : 39.9;]/10, length(dates))

vegperiod(
    dates, 
    Tavg, 
    Menzel("Picea abies (frueh)", est_prev = 2), 
    VonWilpert())
```
