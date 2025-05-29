```
analyze(input, method)
analyze(input, method, output_selection)
```

指定された入力に対してアナライザー `method` を適用し、[`Explanation`](@ref) を返します。`output_selection` が指定されている場合、その出力に対して説明が計算されます。そうでない場合は、最も高い活性化を持つ出力が自動的に選択されます。

詳細は [`Explanation`](@ref) を参照してください。
