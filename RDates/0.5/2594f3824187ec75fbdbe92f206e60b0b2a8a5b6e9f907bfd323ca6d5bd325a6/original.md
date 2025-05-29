```
apply(rounding::HolidayRoundingConvention, date::Dates.Date, calendar::Calendar)::Dates.Date
```

Apply the holiday rounding to a given date. There is no strict requirement that the resolved date will not be a holiday for the given date.
