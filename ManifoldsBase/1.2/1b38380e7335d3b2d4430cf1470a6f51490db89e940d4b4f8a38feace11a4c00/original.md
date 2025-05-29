```
ApproximatelyError{V,S} <: Exception
```

Store an error that occurs when two data structures, e.g. points or tangent vectors.

# Fields

  * `val` amount the two approximate elements are apart – is set to `NaN` if this is not known
  * `msg` a message providing more detail about the performed test and why it failed.

# Constructors

```
ApproximatelyError(val::V, msg::S) where {V,S}
```

Generate an Error with value `val` and message `msg`.

```
ApproximatelyError(msg::S) where {S}
```

Generate a message without a value (using `val=NaN` internally) and message `msg`.
