```
cas_search(query; api_url = "https://commonchemistry.cas.org/api", size=10, offset=0)

Query the CAS Common Chemistry API with query string.
Returns Dict with 2 keys:

* "count": the number of matching records
* "results": vector of Dics describing the first `size` results

keyword arguments

size: number of results to return. The API limits this to 100
offset: number of records to skip. This is used to get records past the first 100
```
