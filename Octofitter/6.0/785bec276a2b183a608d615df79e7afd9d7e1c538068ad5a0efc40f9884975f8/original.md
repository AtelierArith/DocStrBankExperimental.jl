```
HGCAInstantaneousLikelihood(;gaia_id=1234,N_ave=1)
```

Model Hipparcos-Gaia Catalog of Accelerations (Brandt et al) data using a simplified instantaneous model – calculating the proper motion and positions at 1 to N epochs and averaging them.  This is quicker than the full `HGCALikelihood` which involves fitting linear least-squares solutions at each epoch. It should be entirely equivalent for systems without strong acceleration *during* the Hipparcos or Gaia missions. 

Upon first load, you will be prompted to accept the download of the eDR3 version of the HGCA  catalog.
