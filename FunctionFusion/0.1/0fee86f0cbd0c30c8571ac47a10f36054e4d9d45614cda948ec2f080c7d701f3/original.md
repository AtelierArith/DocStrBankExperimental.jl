```
@conditional name::output_artifact = bool_artifact ? input_artifact1 : input_artifact2
```

Defines a `ConditionalProvider` that promotes one of the `input_artifact` to an `output_artifact` depending on a value of `bool_artifact`. The `input_artifact`s and `output_artifact` should be of the same type and `bool_artifact` shall be of type `Bool`

# Example

```
@artifact A = Int
@artifact B = Int
@artifact C = Bool
@artifact D = Int

@conditional conditional::D = C ? A : B
```
