```
get_active_stopping_criteria(c)
```

は、[`StoppingCriterion`](@ref) `c` 内にある、停止を示すすべてのアクティブな停止基準を返します。つまり、その理由が空でない場合です。単純な停止基準の場合、これは停止が示されていない場合は空の配列を返すか、停止基準を配列の唯一の要素として返します。[`StoppingCriterionSet`](@ref) の場合、停止を示すすべての内部（ネストされた）基準が返されます。
