A CDate (short for Calender Date) is defined as 

```julia
CDate = Tuple{DPart, DPart, DPart, DPart}
```

```
A tuple `date` of type `CDate` is unpacked by convention as
(calendar, year, month, day), where `calendar` is one of
```

```julia
"European" 
"Common" 
"Julian" 
"Hebrew" 
"Islamic" 
"IsoDate"
```

```
Alternatively the acronyms
```

```julia
EC, CE, JD, AM, AH, and ID 
```

```
can be used. "Common" or CE denotes the proleptic Gregorian calendar
and `DPart` (date part) is a typename for Int64.
```

```julia
CDateStr(cd::CDate) 
```

The function CDateStr converts a date of type CDate to a string representation, where the  numeric part follows the recommendation of ISO 8601 and is prefixed by one of the acronyms  for the calendar names indicated above. 

Examples for `CDates` and their string representation given by `CDateStr`:

```julia
("European", 2022,  1,  6)  -> "EC-2022-01-06"
("Common",   2022,  1, 19)  -> "CE-2022-01-19"
("Julian",   2022,  1,  6)  -> "JD-2022-01-06"
("Hebrew",   5782, 11, 17)  -> "AM-5782-11-17"
("Islamic",  1443,  6, 15)  -> "AH-1443-06-15"
("IsoDate",  2022,  3,  3)  -> "ID-2022-03-03"
```

The components of a `CDate` can be accessed by applying the functions

```julia
Calendar, Year, Month, Day and Date 
```

to a calendar date.

The function CalendarName(CC) returns the calendar name from a calendar specifier CC.  For example both CalendarName(ID) and CalendarName(6) return the string "IsoDate".
