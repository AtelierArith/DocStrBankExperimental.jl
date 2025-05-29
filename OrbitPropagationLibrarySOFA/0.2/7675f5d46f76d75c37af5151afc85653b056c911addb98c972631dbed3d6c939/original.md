```
dateVec = jdate2datevec(JD)
```

Convert a Julian Date into a date vector

The input values are Julian Date returned in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

A date vector is a length 6 vector of floats with [year, month, day, hour, minute, seconds]

Combines SOFA's `jd2cal` and Vallado (v5) Algorithm 22, Vallado for yr, month, and day (SOFA was giving me day issues), and SOFA for hr, min, sec to preserve seconds precision. Also utilized `d2dtf` from SOFA to handle UTC values
