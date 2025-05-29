```
duration(d1::Date, d2::Date)
```

Compute the duration given two dates, which is the number of years since the first date. The interval `[0,1)` is defined as having  duration `1`. Can return negative durations if second argument is before the first.

```julia
julia> issue_date  = Date(2018,9,30);

julia> duration(issue_date , Date(2019,9,30) ) 
2
julia> duration(issue_date , issue_date) 
1
julia> duration(issue_date , Date(2018,10,1) ) 
1
julia> duration(issue_date , Date(2019,10,1) ) 
2
julia> duration(issue_date , Date(2018,6,30) ) 
0
julia> duration(Date(2018,9,30),Date(2017,6,30)) 
-1
```
