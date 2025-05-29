```julia
struct UA_DiagnosticInfo
```

Fields:

  * `hasSymbolicId`
  * `hasNamespaceUri`
  * `hasLocalizedText`
  * `hasLocale`
  * `hasAdditionalInfo`
  * `hasInnerStatusCode`
  * `hasInnerDiagnosticInfo`
  * `symbolicId`
  * `namespaceUri`
  * `localizedText`
  * `locale`
  * `additionalInfo`
  * `innerStatusCode`
  * `innerDiagnosticInfo`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
