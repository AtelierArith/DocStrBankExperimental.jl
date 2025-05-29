```
genmeta(source_df, s_name="SLURPName")
```

SIPs using the SIP 2.0 Standard (Stochastic Information Packets, Savage[2009]) require that Meta Data be available and maintained. This function creates a file template to add MetaData to your SIP Library. This is a seperate file must accompany the DataFrame to generate the SIP Library correctly. If ommited, the file will export the SIP Library without any metadata.
