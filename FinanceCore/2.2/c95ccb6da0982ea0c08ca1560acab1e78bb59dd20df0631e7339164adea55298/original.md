```
Cashflow(amount,time)
```

A `Cahflow{A,B}` is a contract that pays an `amount` at `time`. 

Cashflows can be:

  * negated with the unary `-` operator.
  * added/subtracted together but note that the `time` must be `isapprox` equal.
  * multiplied/divided by a scalar.

Supertype Hierarchy ≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡

```
Cashflow{A<:Real, B<:Timepoint} <: FinanceCore.AbstractContract <: Any
```
