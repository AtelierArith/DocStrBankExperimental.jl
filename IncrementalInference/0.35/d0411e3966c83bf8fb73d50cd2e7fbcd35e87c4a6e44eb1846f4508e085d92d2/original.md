```julia
getCliqueStatus(cliqdata)

```

Return `::Symbol` status a particular clique is in, with specific regard to solution or numerical initialization status:

  * :needdownmsg
  * UPSOLVED
  * DOWNSOLVED
  * INITIALIZED
  * MARGINALIZED
  * NULL

Notes:

  * `NULL` represents the first uninitialized state of a cliq.
