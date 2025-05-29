```
setinvalid_qualityflag!(df; 
  vars=["LE","H","NEE","Tair","VPD","wind"],
  qc_suffix="_qc",
  good_quality_threshold = 1.0,
  missing_qc_as_bad = true,
  setvalmissing = true, 
)
```

Set records with quality flags indicating problems to false in :valid column. 

# Arguments

  * df: DataFrame with column :GPP

optional

  * `vars=["LE","H","NEE","Tair","VPD","wind"]`: columns to theck for quality
  * `qc_suffix="_qc"`: naming of the corresponding quality-flag column
  * `good_quality_threshold = 1.0`: threshold in quality flag up to which data is considered good quality
  * `missing_qc_as_bad = true`: set to false to not mark records with missing  quality flag as invalid
  * `setvalmissing = true`: set to false to prevent replacing values in value column  corresponding to problematic quality flag to missing.

# Value

df with modified :valid and value columns. 

# Example

```jldoctest; output = false
using DataFrames
df = DataFrame(
  NEE = 1:3, NEE_qc = [1,1,2],
  GPP = 10:10:30, GPP_qc = [1,missing,1])
setinvalid_qualityflag!(df; vars = ["NEE", "GPP"])
df.valid == [true, false, false]
ismissing(df.GPP[2]) && ismissing(df.NEE[3])
# output
true
```
