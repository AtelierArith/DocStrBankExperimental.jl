```
DateFormat(format::AbstractString, locale="english") --> DateFormat
```

When the `TimeZones` package is loaded, 2 extra character codes are available for constructing the `format` string:

| Code | Matches                    | Comment                                                                                             |
|:---- |:-------------------------- |:--------------------------------------------------------------------------------------------------- |
| `z`  | +02:00, -0100, +14         | Parsing matches a fixed numeric UTC offset `±hh:mm`, `±hhmm`, or `±hh`. Formatting outputs `±hh:mm` |
| `Z`  | UTC, GMT, America/New_York | Name of a time zone as specified in the IANA tz database                                            |
