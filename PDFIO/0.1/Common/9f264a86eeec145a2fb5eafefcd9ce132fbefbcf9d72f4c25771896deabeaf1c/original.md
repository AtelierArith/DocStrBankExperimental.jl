```
    CDDate(s::CDTextString)
```

PDF files support the string format: (D:YYYYMMDDHHmmSSOHH'mm)

# Example

```
julia> date = CDDate("D:20190425173659+05'30")
D:20190425173659+05'30

julia> date.d
2019-04-25T17:36:59

julia> date.tz
5 hours, 30 minutes

julia> date.ahead
true
```
