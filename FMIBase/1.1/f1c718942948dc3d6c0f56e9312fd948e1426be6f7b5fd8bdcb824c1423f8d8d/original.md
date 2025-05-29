```
getSimpleTypeAttributeStruct(st::fmi2SimpleType)
```

Returns the attribute structure for the simple type `st`. Depending on definition, this is either `st.Real`, `st.Integer`, `st.String`, `st.Boolean` or `st.Enumeration`.

# Arguments

  * `st::fmi2SimpleType`: Struct which provides the information on custom SimpleTypes.

# Source

  * FMISpec2.0.3 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.3[p.40]: 2.2.3 Definition of Types (TypeDefinitions)
