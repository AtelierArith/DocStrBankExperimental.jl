```
difficulty(header::Header) -> BigInt
```

Returns the header difficulty based on the bits

```
difficulty is (target of lowest difficulty) / (header's target)
lowest difficulty has bits that equal 0xffff001d
```
