```
jd_to_date([T,] JD::Number)
```

Convert the Julian Day `JD` to Gregorian Calendar. The optional parameter `T` defines the return type.

# Returns

If `T` is omitted or `Int`, then a tuple with the following data will be returned:

  * Year.
  * Month (`1` => **January**, `2` => **February**, ...).
  * Day.
  * Hour (0 - 24).
  * Minute (0 - 59).
  * Second (0 - 59).

Notice that if `T` is `Int`, the seconds field will be rounded to an `Int`.  Otherwise, it will be floating point.

If `T` is `Date`, it will return the Julia structure `Date`. Notice that the hours, minutes, and seconds will be neglected because the structure `Date` does not support them.

If `T` is `DateTime`, it will return the Julia structure `DateTime`.

# Remarks

The algorithm was obtained from [1] (accessed on 2022-07-20). In [1], there is the following warning:

!!! note
    This method will not give dates accurately on the Gregorian Proleptic Calendar, i.e., the calendar you get by extending the Gregorian calendar backwards to years earlier than 1582 using the Gregorian leap year rules. In particular, the method fails if Y < 400.


# References

  * **[1]**: https://quasar.as.utexas.edu/BillInfo/JulianDatesG.html
