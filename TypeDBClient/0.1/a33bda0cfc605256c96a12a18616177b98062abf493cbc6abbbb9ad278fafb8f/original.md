```
get_regex(r::RemoteConcept{<:AbstractAttributeType})
```

For AttributeTypes with the value type String it is possible to set a regex pattern to proof the incoming string to fulfill the pattern. Otherwise the insert will fail. The function wil give back a regex string if set. The regex string follows the conventions of the Java programming language.
