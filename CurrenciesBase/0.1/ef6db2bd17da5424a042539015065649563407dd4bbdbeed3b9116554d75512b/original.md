A representation of a monetary value, denominated in some currency. The currency used is part of the type and not the object. The value is internally represented as a quantity of some integer type. The usual way to construct a `Monetary` directly, if needed, is:

```
Monetary(:USD)      # 1.00 USD
Monetary(:USD, 325) # 3.25 USD
```

Be careful about the decimal point, as the `Monetary` constructor takes an integer, representing the number of smallest denominations of the currency. Typically, this constructor is not called directly. It is easier to use the `@usingcurrencies` macro and the `100USD` form instead.

Although this type is flexible enough to support values internally represented as any integer type, such as `BigInt`, it is recommended to use the built-in `Int` type on your architecture unless you need a bigger type. Do not mix different kinds of internal types. To use a different internal representation, change the type of the second argument to `Monetary`:

```
Monetary(:USD, BigInt(100))
```

In some applications, the minor denomination of a currency is not precise enough. It is sometimes useful to override the number of decimal points stored. For these applications, a third type parameter can be provided, indicating the number of decimal points to keep after the major denomination:

```
Monetary{:USD, BigInt, 4}(10000)            # 1.0000 USD
Monetary(:USD, BigInt(10000); precision=4)  # 1.0000 USD
```
