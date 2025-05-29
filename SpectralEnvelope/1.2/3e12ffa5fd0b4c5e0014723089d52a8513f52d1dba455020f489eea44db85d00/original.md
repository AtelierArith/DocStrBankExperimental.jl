```
apply_mapping(ts, mapping)
```

Transforms the input time-series 'ts' according to the mapping 'mapping'. Typically, 'mapping' would be the output of the 'get_mappings' function, although you can provide your own. 'mapping' should be a Dict specifying each value and what it should be mappied to. Example: {"A" : 0.54, "G" : 0.62, "T" : -0.57, "C" : 0.0}

Returns an array which correspond to the mapped series according to 'mapping'
