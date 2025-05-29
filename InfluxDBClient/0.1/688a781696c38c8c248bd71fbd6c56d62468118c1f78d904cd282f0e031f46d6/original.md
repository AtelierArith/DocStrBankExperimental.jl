Creates a String in lineprotocol format given a measuremant name (String) and a DataFrame Defaults used are  influx_precision = 'ns' tzstr = "UTC" # TimeZone string

```julia
df = DataFrame(sensor_id = ["TLM0900","TLM0901","TLM0901"], temperature = [73.9,55.1,22.9], humidity=[14.9,55.2,3], datetime = [now(),now()-Second(51),now()-Second(50)])
lp = lineprotocol("measurement_name",df)
```
