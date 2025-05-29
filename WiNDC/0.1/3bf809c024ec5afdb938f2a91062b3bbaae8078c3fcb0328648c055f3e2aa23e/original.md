```
calibrate(data::AbstractNationalTable)
```

This is currently geared toward calibrating the national dataset. I'll be working to make this be a general calibration function.

Returns a new AbstractNationalTable with the calibrated values and the model.

There are three primary balancing operations:

1. Zero Profit - Column sums are equal
2. Market Clearance - Row sums are equal
3. Margin Balance - The margins balance

The three tax rates are fixed. The tax rates are:

1. Output Tax Rate
2. Absorption Tax Rate
3. Import Tariff Rate

The following are fixed:

1. Labor Compensation
2. Imports
3. Exports
4. Household Supply

Any zero values will remain zero. 
