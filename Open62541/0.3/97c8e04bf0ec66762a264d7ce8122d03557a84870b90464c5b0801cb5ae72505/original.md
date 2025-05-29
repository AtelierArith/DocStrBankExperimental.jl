```julia
struct UA_ValueBackend
```

Fields:

  * `backendType`
  * `backend`

Note that this type is defined as a union type in C; therefore, setting fields of a Ptr of this type requires special care.
