```
struct ITC <: Policy
```

Investment Tax Credit - A tax incentive that is a percentage of capital cost given to generators that meet the qualifications. 

# Keyword Arguments

  * `name`: policy name
  * `values`: the credit level, stored as an OrderedDict with year and value `(:y2020=>0.3)`.  Credit level refers to the percentage of the capex that will be rebated to the investor
  * `gen_filters`: filters for qualifying generators, stored as an OrderedDict with gen table columns and values (`:emis_co2=>"<=0.1"` for co2 emission rate less than or equal to 0.1)
