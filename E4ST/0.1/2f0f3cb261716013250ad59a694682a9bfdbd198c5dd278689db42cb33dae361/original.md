```
create_capex_obj!(config, data) ->
```

Creates capex*obj and transmission*capex*obj columns which are the capex cost seen in the objective function. It is a ByYear column that is only non zero for year*on. Set to capex for unbuilt generators in and after the year_on Set to 0 for already built capacity because capacity expansion isn't considered for existing generators  
