```
sc_uint128_init(a, high, low)
```

Initializes an unsigned 128 bit integer to a given value.

### Parameters

  * `a`:[in,out] A pointer to the [`sc_uint128_t`](@ref) that will be initialized.
  * `high`:[in] The given high bits to initialize *a*.
  * `low`:[in] The given low bits to initialize *a*.

### Prototype

```c
void sc_uint128_init (sc_uint128_t * a, uint64_t high, uint64_t low);
```
