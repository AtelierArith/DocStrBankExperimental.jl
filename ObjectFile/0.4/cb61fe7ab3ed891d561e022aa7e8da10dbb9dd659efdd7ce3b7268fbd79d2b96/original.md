```
@derefmethod
```

Macro to create a method that works on a reference type by generating a wrapper call to `deref(x)` where `x` is the first argument in the call.  Example:

```
@derefmethod foo(x::SectionRef)
```

Will generate the following code:

```
foo(x::SectionRef, args...) = foo(deref(x), args...)
```
