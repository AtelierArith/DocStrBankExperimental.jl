**Get the next page of results**

This function will retrieve the next page of results. By default, it will walk through queries 20 at a time. This can be modified by changing the `.query["limit"]` value, to any value *up to* 300, which is the limit set by GBIF for the queries.

If filters have been applied to this query before, they will be *removed* to ensure that the previous and the new occurrences have the same status, but only for records that have already been retrieved.
