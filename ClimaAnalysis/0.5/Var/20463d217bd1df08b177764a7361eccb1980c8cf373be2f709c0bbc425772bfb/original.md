```
shift_to_start_of_previous_month(var::OutputVar)
```

Shift the times in the time dimension to the start of the previous month.

After applying this function, the start date in the attributes correspond to the first element in the time array.

This function is helpful in ensuring consistency in dates between simulation and observational data. One example of this is when adjusting monthly averaged data. For instance, suppose that data on 2010-02-01 in the `OutputVar` corresponds to the monthly average for January. This function shifts the times so that 2010-01-01 will correspond to the monthly average for January.

Note that this function only works for the time dimension and will not work for the date dimension.
