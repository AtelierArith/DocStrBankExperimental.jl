```
state(ccn) -> String
```

Decode the state code of `ccn` and return it as a `String`.

The first two characters of a CCN encode the "state" where the entity is located. "State" is interpreted loosely, as valid states include countries (like Canada) and territories (like (Guam).

Returns `CMSCertificationNumbers.INVALID_STATE` if the first two characters are not a valid state code.
