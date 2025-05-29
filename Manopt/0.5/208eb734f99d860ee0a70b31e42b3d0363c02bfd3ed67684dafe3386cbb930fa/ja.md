```
StopWhenAny <: StoppingCriterionSet
```

[`StoppingCriterion`](@ref) 要素の配列を格納し、*いずれか* の単一要素が停止を示すときに停止することを示します。`reason` は、すべての理由を連結したもので与えられます（すべての非示唆的なものは `""` を返すと仮定します）。

# コンストラクタ

```
StopWhenAny(c::NTuple{N,StoppingCriterion} where N)
StopWhenAny(c::StoppingCriterion...)
```
