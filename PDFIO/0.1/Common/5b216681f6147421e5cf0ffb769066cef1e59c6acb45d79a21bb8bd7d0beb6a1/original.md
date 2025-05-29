```
    getUTCTime(d::CDDate) -> CDDate
```

Removes the timezone information and returns the CDDate at UTC.

# Example

```
julia> getUTCTime(CDDate("D:20190425173659+05'30"))
D:20190425120659Z
```
