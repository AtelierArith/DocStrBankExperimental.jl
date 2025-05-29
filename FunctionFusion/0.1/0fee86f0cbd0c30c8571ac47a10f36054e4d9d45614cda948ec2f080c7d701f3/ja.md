```
@conditional name::output_artifact = bool_artifact ? input_artifact1 : input_artifact2
```

`ConditionalProvider`を定義し、`bool_artifact`の値に応じて`input_artifact`の1つを`output_artifact`に昇格させます。`input_artifact`と`output_artifact`は同じ型である必要があり、`bool_artifact`は`Bool`型でなければなりません。

# 例

```
@artifact A = Int
@artifact B = Int
@artifact C = Bool
@artifact D = Int

@conditional conditional::D = C ? A : B
```
