```
cas(query; api_url = "https://commonchemistry.cas.org/api", fetch=10, skip = 0, pagesize = 100)

Query the CAS Common Chemistry API with query string.
Returns DataFrame of matching records

From the API description: https://commonchemistry.cas.org/api-overview
* Allows searching by CAS RN (with or without dashes), SMILES (canonical or isomeric), InChI (with or without the "InChI=" prefix), InChIKey, and name
* Searching by name allows use of a trailing wildcard (e.g., car*)
* All searches are case-insensitive

A wild-card query can return a lot of entries taking a long time to fetch. So by default, only the first 10 are fetched. The total number is reported.
Use fetch = :all to unconditionally get all.

query : query string. Will be uri encoded
fetch N: maximal number of recoreds to fetch. An integer of :all.
skip N : Skip first N records
pagesize: Default page-size in CAS API is 100. A lower value can e set. Mostly for debugging
```
