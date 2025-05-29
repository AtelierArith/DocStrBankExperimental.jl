```
importsip(FileName, source="Not specified by user")
```

This function allows to import SIPs in CSV format from Julia using the SIP 2.0 Standard (Stochastic Information Packets, Savage[2009]) to build unified simulation models. Based on the CSV package, the function cleans up meta data and cleans out redundant columns. You can also set a *source string* that will be included in your SIP DataFrame as a dimension.
