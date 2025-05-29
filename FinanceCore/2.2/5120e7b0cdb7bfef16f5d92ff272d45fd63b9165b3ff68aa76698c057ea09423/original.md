```
Composite(A,B)
```

Summary ≡≡≡≡≡≡≡≡≡

```
struct Composite{A, B}
```

A `Composite{A,B}` is a contract that is composed of two other contracts of type `A` and type `B`.  The maturity of the composite is the maximum of the maturities of the two components. 

It is used to assemble arbitrarily complex contracts from simpler ones.

Fields ≡≡≡≡≡≡≡≡

```
a :: A
b :: B
```

Supertype Hierarchy ≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡

```
Composite{A, B} <: FinanceCore.AbstractContract <: Any
```
