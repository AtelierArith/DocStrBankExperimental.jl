```
const IMPLICATION = NamedConnective{:→}()
const → = IMPLICATION
arity(::typeof(→)) = 2
```

論理的含意。 `\to<tab>` で入力できます。

関連情報としては [`NamedConnective`](@ref)、[`Connective`](@ref) を参照してください。
