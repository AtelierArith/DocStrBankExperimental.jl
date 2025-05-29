```
StopWhenAll <: StoppingCriterionSet
```

[`StoppingCriterion`](@ref) 要素の配列を格納し、*すべて* が停止を示すときに停止することを示します。`reason` はすべての理由の連結によって与えられます。

# コンストラクタ

```
StopWhenAll(c::NTuple{N,StoppingCriterion} where N)
StopWhenAll(c::StoppingCriterion,...)
```
