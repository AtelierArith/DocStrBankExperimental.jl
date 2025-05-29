```
WebBLAST(query;
    query_names = nothing,
    max_waits = Inf,
    num_hits = 100,
    database = "nt",
    program = "blastn",
    verbosity = 1, 
    option_string = "",
    save_XML_path = nothing,
    blast_URL = "https://blast.ncbi.nlm.nih.gov/Blast.cgi?")
```

```

NOTE: This relies on querying a public web service, using an API that they list as "deprecated". Please do not count on this working in the long run, and please don't abuse it as that might get it shut down faster.

WHAT YOU PUT IN:

query must be either a String, or an array of String (if searching multiple sequences). These are expected to be nucleotides, or amino acids, but we aren't bothering with specific types for these. Just make sure they match the database and program.

query_names must be nothing (default), in which case your queries will be submitted as query_1, query_2 etc, or a vector of String with as many names as there are queries.

save_XML_path will export the returned XML - you probably don't need this.

max_waits controls the waiting time (20 sec per wait) before timeout occurs.

num_hits controls the maximum number of hits that get returned.

database and program are common blast options you might want to modify. Eg. program = "blastp", database = "pdb".

option_string is any string you want to get injected into the BLAST Put call. Must be of the form "&MATRIX=PAM230&NUCL_REWARD=2" etc 

blast_URL is a string that you can use to point to a different blast service, if you have access to one.

WHAT GETS RETURNED:

[Note: if you CBA to figure out how to traverse all this, just call ```flatten_to_dataframe(WebBLAST(query))``` instead.]

Takes an XML document, returned from BLAST and pushed through EzXML, and converts this to an Array of dictionaries.

The base array has one element per query (with one query, this will be an array of length 1).

Each Query dictionary will have a key "Query_hit_array", which will return an array of hit dictionaries.

Each hit can have more than one "High Similarity Pair" (or "HSP"), so the hit dictionary has a key "Hit_hsps" which itself is an array of HSPs.
```
