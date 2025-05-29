```
@switch_provider Name(Input)::Output = [Options...]
```

Creates switch provider that will map `Input` to switch which of `Options` include in the `Output` If `Output` is a `AbstractVector` or `Tuple` then `Input` had to be iteratable and it will construct it for as many `Input` elements as it has otherwise only one Artifact would be returned
