```
set_regex(r::RemoteConcept{<:AbstractAttributeType},
    regex::Optional{AbstractString})
```

For AttributeTypes with the value type String it is possible to set a regex pattern to check the incoming string matches the pattern, otherwise the insert will fail. The function will set a regex string to a given attribute. The regex string follows the conventions of the Java programming language.
