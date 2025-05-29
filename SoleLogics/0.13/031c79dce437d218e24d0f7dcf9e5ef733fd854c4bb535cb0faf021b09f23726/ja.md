```
struct NamedConnective{Symbol} <: Connective end
```

名前またはシンボルによって定義された接続詞を表すためのシングルトン型です。

# 例

AND接続詞（すなわち論理的な論理積）は、サブタイプとして定義されます：

```
const CONJUNCTION = NamedConnective{:∧}()
const ∧ = CONJUNCTION
arity(::typeof(∧)) = 2
```

他にも [`NEGATION`](@ref)、[`CONJUNCTION`](@ref)、[`DISJUNCTION`](@ref)、[`IMPLICATION`](@ref)、[`Connective`](@ref) を参照してください。
