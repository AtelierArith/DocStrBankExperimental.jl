```
leftmost(d::Derivation, prod::AbstractArray{Production})::Derivation
```

*左最*の導出ステップを実行します。指定された生成を文の形の現在の最左の非終端記号に対して、一つずつ適用します。
